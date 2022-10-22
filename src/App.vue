<template>
  <div id="app">
    <GithubProfile/>
  </div>
</template>

<script>
import GithubProfile from './components/GithubProfile.vue'

export default {
  name: 'App',
  components: {
    GithubProfile
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
