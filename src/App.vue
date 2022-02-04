<template>
  <!-- <div class="test">
    <h1>Library VueJS Project</h1>
  </div> -->
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
  @import url('https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200;0,300;0,400;0,600;0,700;0,800;1,400&display=swap');

  body {
    font-family: 'Nunito Sans', sans-serif !important;
    padding: 0;
    margin: 0;
    background-color: #eef2f7;
  }


  /* // .test {
  //   font-family: 'Nunito Sans', sans-serif;
  //   h1 {
  //     font-size: 32px;
  //   }
  // } */
</style>
