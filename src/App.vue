<template>
  <h1>Library VueJS Project</h1>
  <add-book-form></add-book-form>
</template>

<script>
import AddBookForm from './components/AddBookForm.vue'
import EditBookModal from './components/EditBookModal.vue'

export default {
  name: 'App',
  components: { 
    AddBookForm, EditBookModal
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
