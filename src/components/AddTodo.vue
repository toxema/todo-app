<template>
  <div class="d-flex justify-content-between align-items-center p-1">
    <input v-model="todotext" type="email" class="form-control" id="exampleFormControlInput1" placeholder="Add new Todo" />

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
        this.$emit("add-todo", new Date().toString());
      } else {
        this.$emit("add-todo", this.todotext);
      }
      this.todotext = "";
    },
  },
};
</script>