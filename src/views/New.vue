<template>
  <div>
    <h1>New Word</h1>
    <form action="" @submit.prevent="onSubmit">
      <div class="ui labeled input fluid">
        <div class="ui label"><i class="united kingdom flag"></i> English</div>
        <input type="text" required v-model="word.english" />
      </div>
      <br />
      <div class="ui labeled input fluid">
        <div class="ui label"><i class="germany flag"></i> German</div>
        <input type="text" required v-model="word.german" />
      </div>
      <br />
      <button class="ui primary button">Submit</button>
    </form>
  </div>
</template>

<script>
import { ref } from "vue";
import { useRouter } from "vue-router";
import { addNewWord } from "../helpers/api";

export default {
  name: "New",
  setup() {
    const word = ref({});
    const router = useRouter();

    const onSubmit = async () => {
      //call API to add new word
      await addNewWord(word.value);

      //redirect to word list page
      router.push("/words");
    };

    return {
      word,
      onSubmit,
    };
  },
};
</script>
