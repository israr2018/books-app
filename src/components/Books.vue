<template>
  <div>
    <h2>My Book List</h2>
    <div v-for="book in books" v-bind:key="book.id">
      <book-item :book="book" @del-book="delBook" @edit-book="editBook" />
    </div>
  </div>
</template>

<script>
import BookItem from "./BookItem.vue";
export default {
  components: { BookItem },
  name: "Books",
  props: ["books"],
  emits: ["del-book", "edit-book"],
  methods: {
    delBook(id) {
      this.$emit("del-book", id);
    },
    editBook(id) {
      console.log("%cBooks.vue line:22 id", "color: #007acc;", id);
      this.$emit("edit-book", id);
    },
  },
};
</script>
