<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h2></h2>
    <post-list></post-list>
  </div>
</template>

<script>
// @ is an alias to /src
import PostList from '../components/PostList.vue';

export default {
  name: "Home",
  components: {PostList}
};
</script>

<style>
img {
  width: 70px;
  margin-top: 20px;
}
</style>
