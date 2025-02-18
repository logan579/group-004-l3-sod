<template>
  <img alt="Vue logo" src="../src/assets/icons/logo.png" width="500" height="300">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <WelcomePage />
</template>

<script>
import WelcomePage from './components/WelcomePage.vue'

export default {
  name: 'App',
  components: {
    WelcomePage
  }
}
</script>

<style>
#App { background-color: black;}
</style>
