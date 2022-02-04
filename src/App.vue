<template>
  <div class="test">
    <h1>Library VueJS Project</h1>
  </div>
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

<style lang="scss">
  .test {
    background-color: red;
    text-align: center;

    h1 {
      color: yellow;
    }
  }


  body {
    background: lightblue;
  }
</style>
