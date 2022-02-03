<template>
  <li
      class="book-card"
      v-for="(book, index) in myLibrary"
      v-bind:key="book.id"
    >
      <h3>{{ book.title }}</h3>
      <p>Author: {{ book.author }}</p>
      <p>Pages: {{ book.pages }}</p>
      <p>Status: {{ book.status }}</p>
    <!-- <button @click="this.myLibrary.splice(index, 1)"> -->
    <button @click="deleteBook(book, index)">
      Delete
    </button>
    </li>
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