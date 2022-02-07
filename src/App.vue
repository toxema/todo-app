<template>
  <div class="">
    <div class="fix bg-dark p-2">
      <HeaderBar msg="Todo Vue.js App | eccsistem " />
    </div>
    <div class="container shadow-sm w-75 p-1">
      <add-todo @add-todo="addTodo($event)" />
      <todo-list :datam="todoItems" @delete-item="deleteItem($event)" />
    </div>
  </div>
</template>

<script>
import HeaderBar from "@/components/HeaderBar.vue";
import TodoList from "@/components/TodoList.vue";
import AddTodo from "@/components/AddTodo.vue";

export default {
  name: "App",
  components: {
    HeaderBar,
    TodoList,
    AddTodo,
  },
  provide() {
    return {
      apim: this,
    };
  },
  methods: {
    deleteItem(item) {
      this.todoItems = this.todoItems.filter((i) => i.id != item.id);
    },
    saveTodo(data) {
      console.log("save-todo", data);
    },
     test(data) {
      console.log("test-todo", data);
    },
    addTodo(item) {
      this.todoItems.push({
        id: new Date(),
        text: item,
      });
    },
  },
  data() {
    return {
      todoItems: [
        { id: new Date(), text: " Todo App content #2.0" },
        { id: new Date(), text: " Todo App content #2.1" },
        { id: new Date(), text: " Todo App content #2.2" },
        { id: new Date(), text: " Todo App content #2.3" },
        { id: new Date(), text: " Todo App content #2.4" },
        { id: new Date(), text: " Todo App content #2.5" },
        { id: new Date(), text: " Todo App content #2.6" },
      ],
    };
  },
};
</script>

<style>
</style>
