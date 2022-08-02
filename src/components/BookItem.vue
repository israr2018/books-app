<template>
  <div class="float-left">
    <span class="float-right">
      {{ book.title }}
      <button @click="delBook(book.id)">
        <i class="glyphicon glyphicon-trash">delete</i>
      </button>
      <button @click="editBook(book.id)">
        <i class="glyphicon glyphicon-trash">edit</i>
      </button>
    </span>
  </div>
</template>
<script>
export default {
  name: "BookItem",
  props: ["book"],
  emits: ["del-book", "edit-book"],
  methods: {
    delBook(id) {
      //send to parent
      this.$emit("del-book", id);
    },
    editBook(id) {
      //send to parent
      this.$emit("edit-book", id);
    },
  },
};
</script>
