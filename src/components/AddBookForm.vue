<template>
  <!-- <EditBookModal /> -->
  <form @submit.prevent="addNewBook">
    <label>Add a new book</label>
    <input v-model="bookTitle" type="text" placeholder="Title" required>
    <input v-model="bookAuthor" type="text" placeholder="Author" required>
    <input v-model="bookPages" type="number" placeholder="Number of pages">
    <select v-model="bookStatus" required>
      <option disabled value="">Have you read it?</option>
      <option value="Read">Yes</option>
      <option value="Not Read">No</option>
    </select>
    <button type="submit" id="submit">New Book</button>
  </form>
  <!-- <p>{{ myLibrary }}</p> -->
  <!-- <p>Array length: {{ myLibrary.length }}</p> -->
  
  <ul>
    <li
      class="book-card"
      v-for="(book, index) in myLibrary"
      v-bind:key="book.id"
    >
      <h3>{{ book.title }}</h3>
      <p>Author: {{ book.author }}</p>
      <p>Pages: {{ book.pages }}</p>
      <p>Status: {{ book.status }}</p>

      <button @click="deleteBook(book, index)">
        Delete
      </button>
      <!-- <button @click="showModal = true" class="btn-edit"> -->
      <button @click="editBook(bk, indx)" class="btn-edit">
        Edit
      </button>

      <edit-book-modal 
        :book-title="book.title" 
        :book-author="book.author"
        v-if="showModal" 
        @close="showModal = false">
      </edit-book-modal>
    </li>
  </ul>
</template>

<script>
import EditBookModal from './EditBookModal.vue'

export default {
  name: 'AddBookForm',
  components: { 
    EditBookModal
  },
  data() {
    return {
      bookTitle: '',
      bookAuthor: '',
      bookPages: 0,
      bookStatus: '',
      myLibrary: [
        {
          id: 1,
          title: 'Harry Potter',
          author: 'J.K. Rowling',
          pages: 650,
          status: 'Read'
        },
        {
          id: 2,
          title: 'Game of Thrones',
          author: 'G.R.R. Martin',
          pages: 800,
          status: 'Read'
        }
      ],
      showModal: false
    }
  },
  methods: {
    addNewBook() {
      let lastBookId = this.myLibrary[this.myLibrary.length - 1]
      this.myLibrary.push(
        { 
          id: lastBookId.id+1, 
          title: this.bookTitle,
          author: this.bookAuthor,
          pages: this.bookPages,
          status: this.bookStatus
        }
      )
    },
    deleteBook(id, index) {
      if(confirm('Are you sure?')) {
        this.myLibrary.splice(index, 1)
      }
    },
    editBook(bk, indx) {

        this.showModal = true
      // this.myLibrary.title = book
    }
  }
}
</script>

<style>
  form {
    background-color: #313a46;
    padding: 40px;
    text-align: center;
  }

  label {
    font-size: 24px;
    display: block;
    line-height: 1.2em;
    margin-bottom: 16px;
    color: white;
  }

  input, select {
    padding: 16px;
    border: 1px solid black;
    border-radius: 3px;
    margin: 10px;
  }

  button {
    padding: 16px 40px;
    background-color: lightskyblue;
    font-size: 12px;
    text-transform: uppercase;
    font-weight: 600;
    letter-spacing: 0.5px;
    color: black;
    border: 1px solid black;
    display: block;
    margin: 16px auto 0;
    border-radius: 3px;
    cursor: pointer;
  }

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

  button.btn-edit {
    background-color: green;
  }
</style>