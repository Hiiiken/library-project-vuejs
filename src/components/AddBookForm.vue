<template>
  <p>{{myLibrary}}</p>
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
          <div class="sidebar-widget widget-library-log">
            <library-log
              :my-library="myLibrary.length"
              
            >
            </library-log>
          </div>
        </div>
      </div>

      <div class="col col-9 col-xl">
        <div class="main-content">
            <h1 class="sec-title">My Books</h1>
            <div class="book-list">
              <ul class="grid">
                  <single-book
                    v-for="(book, index) in myLibrary"
                    v-bind:key="book.id"
                    :book-title="book.title"
                    :book-author="book.author"
                    :book-pages="book.pages"
                    :book-status="book.status"
                    @delete="deleteBook(book, index)"
                    @save="saveEditedBook(book, index)">
                  </single-book>
              </ul>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SingleBook from './SingleBook.vue'
import EditBookModal from './EditBookModal.vue'
import LibraryLog from './LibraryLog.vue'

export default {
  name: 'AddBookForm',
  components: { 
    SingleBook, EditBookModal, LibraryLog
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
      newbookTitle: '',
      newbookAuthor: '',
      newbookPages: 0,
      newbookStatus: ''
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
    saveEditedBook(bk, index) {
      // bk.title = bk.title
      // bk.author = 'AUTHORTEST'
      // bk.pages = 0
      // bk.status = 'FINISHED'
      // this.myLibrary.splice(index, 1, bk)

      this.myLibrary.push(
        { 
          id: bk.id, 
          title: bk.title,
          author: bk.author,
          pages: bk.pages,
          status: bk.status
        }
      )
    }
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200;0,300;0,400;0,600;0,700;0,800;1,400&display=swap');

  // PLACEHOLDER STYLES
  ::-webkit-input-placeholder { /* Chrome/Opera/Safari */
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    color: #98a6ad;
  }
  ::-moz-placeholder { /* Firefox 19+ */
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    color: #98a6ad;;
  }
  :-ms-input-placeholder { /* IE 10+ */
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    color: #98a6ad;;
  }
  :-moz-placeholder { /* Firefox 18- */
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    color: #98a6ad;;
  }

  .sidebar {
    background-color: #313a46;
    height: 100vh;
    padding: 50px 40px;
    margin-left: 12px * -1;
    margin-right: 12px * -1;

    h2 {
      color: white;
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

  input {
    width: 100%;
    outline: none;
    height: 46px;
    padding-left: 15px;
    border: 1px solid transparent;
    margin-bottom: 20px;
    border-radius: 0;
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    color: black;
    font-weight: 500;

    &:focus {
      background-color: #f8f8f8;
    }
  }

  select {
    width: 100%;
    outline: none;
    height: 46px;
    padding-left: 10px;
    border: 1px solid transparent;
    margin-bottom: 20px;
    border-radius: 0;
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    color: black;
    font-weight: 500;
  }

  button[type=submit], button[type=button] {
    width: 100%;
    height: 46px;
    border: none;
    border-radius: 0;
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    color: white;
    font-weight: 600;
    background-color: #03b5e6;
    transition: .3s all;

    &:hover {
      background-color: #00a3d0;
      cursor: pointer;
    }
  }

  .sec-title {
    font-size: 26px;
    line-height: 1.3em;
    margin-bottom: 20px;
    font-weight: 600;
    font-family: 'Nunito', sans-serif;
    color: black;
  }

  .main-content {
    padding: 50px 40px;
    margin-left: 12px * -1;
    margin-right: 12px * -1;

    

    @media only screen and (max-width: 480px) {
      padding: 30px 30px;
    }
  }
</style>