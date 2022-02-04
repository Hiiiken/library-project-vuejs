<template>
    <li>
      <h3>{{ bookTitle }}</h3>
      <p>Author: {{ bookAuthor }}</p>
      <p>Pages: {{ bookPages }}</p>
      <p>Status: {{ bookStatus }}</p>

      <button @click="$emit('delete')">
        Delete
      </button>
      <button @click="editBook" class="btn-edit">
        Edit
      </button>

      <edit-book-modal 
        :book-title="bookTitle" 
        :book-author="bookAuthor"
        :book-pages="bookPages"
        :book-status="bookStatus"
        v-if="showModal" 
        @close="showModal = false">
      </edit-book-modal>
    </li>
</template>

<script>
import EditBookModal from './EditBookModal.vue'

export default {
  name: 'SingleBook',
  props: ['bookTitle', 'bookAuthor', 'bookPages', 'bookStatus'],
  data() {
    return {
      showModal: false
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