<template>
  <div class="d-flex justify-content-between align-items-center p-1">
    <input v-model="todotext" @keydown.enter="addItem" class="form-control" placeholder="Add new Todo" />

    <button class="m-2 btn btn-danger" @click="addItem">Add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todotext: "",
    };
  },
  methods: {
    addItem() {
      if (this.todotext == "") {
        this.$emit("add-todo", "Yeni bir Todo " + new Date().getSeconds());
      } else {
        this.$emit("add-todo", this.todotext);
      }
      this.todotext = "";
    },
  },
};
</script>
