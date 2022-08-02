<template>
  <div>
    <add-book-item @add-book="addBook" :editBook="editBook" :edit="edit" />
    <books
      :books="books"
      @del-book="deleteBookItem"
      @edit-book="editBookItem"
    />
  </div>
</template>

<script>
import AddBookItem from "./components/AddBookItem.vue";
import Books from "./components/Books.vue";

export default {
  name: "App",
  components: {
    Books,
    AddBookItem,
  },
  data() {
    return {
      books: [
        { id: 1, title: "Road To VueJS" },
        { id: 2, title: "Road To React" },
      ],
      editBook: {
        title: "",
        id: "",
      },
      edit: false,
      editBookId: "",
    };
  },
  methods: {
    addBook(title) {
      if (this.edit) {
        const index = this.books.findIndex(
          (book) => book.id === this.editBook.id
        );

        this.books[index].title = title;
        this.edit = false;
        return;
      }
      this.books.unshift(this.createBook(title));
      this.edit = true;
    },
    createBook(title) {
      return { id: 3, title };
    },
    deleteBookItem(id) {
      this.books = this.books.filter((book) => book.id !== id);
    },
    editBookItem(id) {
      this.editBook = { ...this.books.find((x) => x.id === id) };
      this.edit = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
