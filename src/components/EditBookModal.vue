<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <h2 class="modal-title">Edit '{{ bookTitle }}' Book Information</h2>
            <div class="popup-close" @click="$emit('close')">×</div>
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

<style lang="scss" scoped>
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
    transition: all .3s ease-in-out;
    font-family: 'Nunito', sans-serif;
    position: relative;
  }

  .modal-header {
    .modal-title {
      margin-bottom: 24px;
      color: black;
      font-size: 20px;
      line-height: 1.5em;
      font-family: 'Nunito', sans-serif;
      font-weight: 600;
      border-bottom: 1px solid #eef2f7;
      padding-bottom: 8px;
    }

    .popup-close {
      position: absolute;
      top: 16px;
      right: 16px;
      cursor: pointer;
      font-size: 26px;
      font-weight: bold;
      line-height: .5em;
      color: #98a6ad;
      transition: all .3s;
    }
  }
  

  label {
    margin-bottom: 8px;
    display: inline-block;
    color: #98a6ad;
  }

  input {
    width: 100%;
    outline: none;
    height: 46px;
    padding-left: 15px;
    border: 1px solid #98a6ad;
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
    border: 1px solid #98a6ad;
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

  .modal-footer {
    display: flex;
    align-items: center;
    margin-top: 8px;

    button {
      height: 46px;
      border: none;
      border-radius: 0;
      font-family: 'Nunito', sans-serif;
      font-size: 14px;
      font-weight: 600;
      transition: .3s all;
      padding: 0 32px;
      cursor: pointer;
    }

    .modal-button-save {
      background-color: #03b5e6;
      margin-right: 16px;
      color: white;

      &:hover {
        background-color: #00a3d0;
      }
    }

    .modal-button-cancel {
      background: #98a6ad;
      // border-color: #98a6ad;
      color: white;

      &:hover {
        opacity: .7;
      }
    }
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