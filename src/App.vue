<template>
  <div>
    <div class="ui menu">
      <div class="header item">Demo Web COMP1842 - CO1303</div>
      <router-link to="/words" class="item"> <i class="list icon"></i>Words </router-link>
      <router-link to="/words/new" class="item">
        <i class="plus icon"></i>New
      </router-link>
    </div>

    <div class="ui container">
      <div class="ui grid">
        <div class="row">
          <div class="twelve wide column">
            <router-view></router-view>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
};
</script>
