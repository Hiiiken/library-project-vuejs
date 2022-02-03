<template>
  <ul>
    <li
      class="book-card"
      v-for="(book, index) in myLibrary"
      v-bind:key="book.id"
    >
    {{ book.title }}
    <!-- <button @click="this.myLibrary.splice(index, 1)"> -->
    <button @click="deleteBook(book, index)">
      Delete
    </button>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'SingleBook',
}
</script>

<style>
  ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .book-card {
    background-color: #eee;
    padding: 24px;
    margin: 16px auto;
    max-width: 650px;
    text-align: left;
  }

  .book-card button {
    margin: 16px 0 0 0;
    padding: 8px 16px;
    background-color: crimson;
    color: white;
  }
</style>