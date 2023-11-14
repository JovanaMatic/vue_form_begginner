<template>
  <base-card>
    <the-form></the-form> 
  </base-card>
</template>

<script>
import TheForm from './components/TheForm.vue'

export default {
  name: 'App',
  components: {
    TheForm
  }
}
</script>

<style>

body {
  background-color: rgb(63, 156, 63);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
