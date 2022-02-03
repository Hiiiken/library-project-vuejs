<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            default header
          </div>

          <div class="modal-body">
            default body
            <form>
              <input v-model="bookTitle" type="text" placeholder="Title" required>
              <input v-model="bookAuthor" type="text" placeholder="Author" required>
              <!-- <input v-model="bookPages" type="number" placeholder="Number of pages">
              <select v-model="bookStatus" required>
                <option disabled value="">Have you read it?</option>
                <option value="Read">Yes</option>
                <option value="Not Read">No</option>
              </select> -->
            </form>
          </div>

          <div class="modal-footer">
            <button class="modal-default-button" @click="$emit('close')">
              Close
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
  props: ['bookTitle', 'bookAuthor']
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
    width: 600px;
    margin: 0 auto;
    padding: 32px;
    background-color: white;
    border-radius: 2px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
    transition: all 0.3s ease;
    font-family: 'Montserrat', sans-serif;
  }

  .modal-header h3 {
    margin-top: 0;
    color: #42b983;
  }

  .modal-body {
    margin: 20px 0;
    padding: 10px;
    background-color: #eee;
  }

  form {
    text-align: left;
  }

  button {
    padding: 16px 40px;
    background-color: blueviolet;
    font-size: 12px;
    text-transform: uppercase;
    font-weight: 600;
    letter-spacing: 0.5px;
    color: white;
    border: 1px solid black;
    display: block;
    margin: 16px auto 0;
    border-radius: 3px;
    cursor: pointer;
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