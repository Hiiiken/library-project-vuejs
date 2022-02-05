<template>
    <li class="col col-4 col-lg">
      <div class="book-card">
        <h3 class="title">{{ bookTitle }}</h3>
        <p class="author">Author: <span>{{ bookAuthor }}</span></p>
        <p class="pages">Pages: <span>{{ bookPages }}</span></p>
        <p class="status">Status: <span>{{ bookStatus }}</span></p>
        <hr>
        <button @click="editBook" class="btn btn-edit">
          Edit
        </button>
        <button @click="$emit('delete')" class="btn btn-delete">
          Delete
        </button>

        <edit-book-modal 
          :book-title="bookTitle" 
          :book-author="bookAuthor"
          :book-pages="bookPages"
          :book-status="bookStatus"
          v-if="showModal" 
          @close="showModal = false"
          @save="$emit('save')">
        </edit-book-modal>
      </div>
    </li>
</template>

<script>
import EditBookModal from './EditBookModal.vue'

export default {
  name: 'SingleBook',
  props: ['bookTitle', 'bookAuthor', 'bookPages', 'bookStatus'],
  data() {
    return {
      showModal: false,
      newbookTitle: '',
      newbookAuthor: '',
      newbookPages: 0,
      newbookStatus: ''
    }
  },
  components: {
    EditBookModal
  },
  methods: {
    editBook() {
      this.showModal = true
    }
  }
}
</script>

<style lang="scss">
  .book-card {
    background: #fff;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 1px 1px 50px 1px rgba(154, 161, 171, .15);
    margin-bottom: 24px;

    .title {
      color: #6c757d;
      font-size: 18px;
      line-height: 1.5em;
      margin-bottom: 5px;
      font-family: 'Nunito', sans-serif;
      font-weight: 700;
    }

    .author, .pages, .status {
      color: #98a6ad;
      font-size: 16px;
      line-height: 1.5em;
      font-family: 'Nunito', sans-serif;
      font-weight: 500;

      span {
        color: #6c757d;
      }
    }

    .status.status--read {
      color: #03b5e6;
    }

    hr {
      border-top: 1px;
      border-color: #eef2f7;
      margin: 12px 0 4px;
    }

    .btn {
      margin-top: 10px;
      background: transparent;
      border: none;
      outline: none;
      cursor: pointer;
      padding: 0;
      font-size: 14px;
      font-family: 'Nunito', sans-serif;
      font-weight: 600;
      color: #6c757d;

      &.btn-delete {
        color: #fa5c7c;
        margin-left: 10px;
        background: url('../assets/delete.svg') no-repeat;
        padding: 0 0 0 24px;

        &:hover {
          color: #f72e56;
          opacity: .9;
        }
      }

      &.btn-edit {
        background: url('../assets/pen.svg') no-repeat;
        padding: 0 0 0 24px;
        color: #313a46;

        &.btn-edit:hover {
          color: #000;
          opacity: .9;
        }
      }
    }
  }
</style>