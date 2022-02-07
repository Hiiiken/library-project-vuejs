<template>
  <h2 class="sec-title">Library log</h2>
  <div class="library-log">
    <div class="library-log--single">
      <img src="../assets/book-mark.svg" alt="books icon">
      <h4>Total books : <span>{{ myLibrary }}</span></h4>
    </div>
    <div class="library-log--single">
      <img src="../assets/check.svg" alt="books icon">
      <h4>Books read : <span>{{ booksRead }}</span></h4>
    </div>
    <div class="library-log--single">
      <img src="../assets/x.svg" alt="books icon">
      <h4>Books not read : <span>{{ booksNotRead }}</span></h4>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LibraryLog',
  props: ['myLibrary', 'booksRead', 'booksNotRead'],
}
</script>

<style lang="scss">
  .library-log  {
    background-color: #404853;
    padding: 20px;
    border-radius: 5px;
    text-align: left;
    color: #fff;

    .library-log--single {
      display: flex;
      align-items: center;

      img {
        width: 32px;
        vertical-align: middle;
        margin-right: 10px;
      }

      h4 {
        font-weight: 500;
        line-height: 1.5em;
        text-transform: uppercase;
        font-size: 14px;
      }

      span {
        font-weight: 400;
        color: #03b5e6;
      }
    }
  }
</style>