<template>
  <h1>Library VueJS Project</h1>
  <AddBookForm />
  <!-- <SingleBook /> -->
</template>

<script>
import AddBookForm from './components/AddBookForm.vue'
// import SingleBook from './components/SingleBook.vue'

export default {
  name: 'App',
  components: { 
    AddBookForm
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
