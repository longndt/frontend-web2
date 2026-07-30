<template>
  <div>
    <h1>Word List</h1>
    <table class="ui blue table">
      <thead>
        <tr>
          <th>English</th>
          <th>German</th>
          <th colspan="3">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(word, index) in words" :key="index">
          <td>{{ word.english }}</td>
          <td>{{ word.german }}</td>

          <td width="75">
            <router-link
              class="ui button green"
              :to="{ name: 'Show', params: { id: word._id } }"
              >Show</router-link
            >
          </td>
          <td width="75">
            <router-link
              class="ui button yellow"
              :to="{ name: 'Edit', params: { id: word._id } }"
              >Edit</router-link
            >
          </td>
          <td width="75">
            <a @click.prevent="onDelete(word._id)" class="ui red button">Delete</a>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import { viewAllWords, deleteWord } from "../helpers/api";

export default {
  name: "Words",
  setup() {
    const words = ref([]);

    onMounted(async () => {
      words.value = (await viewAllWords()) || [];
    });

    const onDelete = async (id) => {
      const deleteConfirm = window.confirm("Are you sure to delete this word?");
      if (deleteConfirm) {
        await deleteWord(id);
        words.value = words.value.filter((word) => word._id !== id);
      }
    };

    return {
      words,
      onDelete,
    };
  },
};
</script>
