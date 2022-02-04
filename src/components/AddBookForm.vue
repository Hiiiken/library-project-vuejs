<template>
  <div class="container-fl">
    <div class="grid">
      <div class="col col-3 col-xl">
        <div class="sidebar">
          <div class="sidebar-widget">
            <h2 class="sec-title">Add a new book</h2>
            <form @submit.prevent="addNewBook" class="add-book-form">
              <!-- <label>Add a new book</label> -->
              <input v-model="bookTitle" type="text" placeholder="Title" required>
              <input v-model="bookAuthor" type="text" placeholder="Author" required>
              <input v-model="bookPages" type="number" placeholder="Number of pages">
              <select v-model="bookStatus" required>
                <option disabled value="">Have you read it?</option>
                <option value="Read">Yes</option>
                <option value="Not Read">No</option>
              </select>
              <button type="submit" class="btn btn-submit" id="submit">New Book</button>
            </form>
          </div>
        </div>
      </div>

      <div class="col col-9 col-xl">
        <div class="main-content">
            <h1 class="sec-title">My Books</h1>
            <div class="book-list">
              <ul class="grid">
                  <single-book
                    class="col col-4 col-lg book-card"
                    v-for="(book, index) in myLibrary"
                    v-bind:key="book.id"
                    :book-title="book.title"
                    :book-author="book.author"
                    :book-pages="book.pages"
                    :book-status="book.status"
                    @delete="deleteBook(book, index)"
                  >
                  </single-book>
              </ul>
            </div>
        </div>
      </div>
    </div>
  </div>

  <!-- <ul>
    <single-book
      class="book-card"
      v-for="(book, index) in myLibrary"
      v-bind:key="book.id"
      :book-title="book.title"
      :book-author="book.author"
      :book-pages="book.pages"
      :book-status="book.status"
      @delete="deleteBook(book, index)"
    >
    </single-book>
  </ul> -->

  <!-- <ul>
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
  </ul> -->
</template>

<script>
import SingleBook from './SingleBook.vue'
import EditBookModal from './EditBookModal.vue'

export default {
  name: 'AddBookForm',
  components: { 
    SingleBook, EditBookModal
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
      ]
      // showModal: false
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
    }
  }
}
</script>

<style lang="scss">
  .sidebar {
    background-color: #313a46;
    height: 100vh;
    padding: 50px 40px;
    margin-left: 12px * -1;
    margin-right: 12px * -1;

    h2 {
      color: #fff;
    }

    .sidebar-widget {
      margin-bottom: 50px;
    }

    @media only screen and (max-width: 1200px) {
      height: auto;
      display: flex;
      justify-content: space-between;

      .sidebar-widget {
          width: 100%;
          margin-bottom: 0;
      }

      .widget-library-log {
          margin-left: 24px;
      }
    }

    @media only screen and (max-width: 624px) {
      display: block;

      .widget-library-log {
          margin-left: 0;
          margin-top: 30px;
      }
    }

    @media only screen and (max-width: 480px) {
      padding: 30px 30px;
    }
  }
</style>