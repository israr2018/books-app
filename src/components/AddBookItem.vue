<template>
  <div>
    <form @submit="addBook">
      <input
        type="text"
        name="title"
        v-model="title"
        placeholder="please enter book title"
      />
      <button type="submit">{{ edit === true ? "update" : "Add" }}</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddBookItem",
  props: ["editBook", "edit"],
  emits: ["add-book"],
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addBook(e) {
      e.preventDefault();
      this.$emit("add-book", this.title);
      this.title = "";
    },
  },
  watch: {
    editBook: {
      handler() {
        this.title = this.editBook.title;
      },
    },
  },
};
</script>
