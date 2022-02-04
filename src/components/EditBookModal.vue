<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <h2 class="modal-title">Edit '{{ bookTitle }}' Book Information</h2>
          </div>

          <div class="modal-body">
            <form>
              <label for="book-title">Book Title</label>
              <input v-model="bookTitle" id="book-title" type="text" placeholder="Title" required>
              <label for="book-author">Author Name</label>
              <input v-model="bookAuthor" id="book-author" type="text" placeholder="Author" required>
              <label for="book-pages">Number of Pages</label>
              <input v-model="bookPages" id="book-pages" type="number" placeholder="Number of pages">
              <label for="book-status">Have You Read It?</label>
              <select v-model="bookStatus" id="book-status" required>
                <option disabled value="">Have you read it?</option>
                <option value="Read">Yes</option>
                <option value="Not Read">No</option>
              </select>
            </form>
          </div>

          <div class="modal-footer">
            <button class="modal-button-save" @click="$emit('save')">
              Save
            </button>
            <button class="modal-button-cancel" @click="$emit('close')">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'EditBookModal',
  props: ['bookTitle', 'bookAuthor', 'bookPages', 'bookStatus']
}
</script>

<style scoped>
  .modal-mask {
    position: fixed;
    z-index: 9998;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: table;
    transition: opacity 0.3s ease;
  }

  .modal-wrapper {
    display: table-cell;
    vertical-align: middle;
  }

  .modal-container {
    box-sizing: border-box;
    width: 600px;
    margin: 0 auto;
    padding: 32px;
    background-color: white;
    border-radius: 4px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
    transition: all 0.3s ease;
    font-family: 'Nunito Sans', sans-serif;
  }

  .modal-header .modal-title {
    margin-top: 0;
    color: #6c757d;
  }

  .modal-body form {
    text-align: left;
    padding: 16px 16px 0;
    margin-bottom: 8px;
  }

  .modal-body form label {
    font-size: 12px;
    margin-bottom: 8px;
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: .5px;
  }

  .modal-body input, select {
    width: 100%;
    box-sizing: border-box;
    margin: 0 0 16px;
  }

  .modal-footer {
    display: flex;
    align-items: center;
  }

  .modal-footer button {
    padding: 16px 40px;
  }

  .modal-button-save {
    background: lightskyblue;
    margin-right: 8px;
    color: black;
  }

  .modal-button-cancel {
    background: #98a6ad;
    border-color: #98a6ad;
    color: white;
  }

  /*
  * The following styles are auto-applied to elements with
  * transition="modal" when their visibility is toggled
  * by Vue.js.
  *
  * You can easily play with the modal transition by editing
  * these styles.
  */

  .modal-enter {
    opacity: 0;
  }

  .modal-leave-active {
    opacity: 0;
  }

  .modal-enter .modal-container,
  .modal-leave-active .modal-container {
    -webkit-transform: scale(1.1);
    transform: scale(1.1);
  }
</style>