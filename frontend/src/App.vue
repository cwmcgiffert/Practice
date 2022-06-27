<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <GetUsers/>
  <PostUsers/>

</template>

<script>
import GetUsers from './components/GetUsers.vue'
import PostUsers from './components/PostUsers.vue'

export default {
  name: 'App',
  components: {
    GetUsers,
    PostUsers
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
