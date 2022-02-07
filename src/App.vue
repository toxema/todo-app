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
import axios from "axios";

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
  mounted() {
    this.getTodos();
  },
  methods: {
    getTodos() {
      axios.get("http://localhost:3000/todos").then((response) => {
        console.log(response);
        this.todoItems = response.data;
      });
    },
    deleteItem(item) {
      axios.delete(`http://localhost:3000/todos/${item.id}`).then((response) => {
        console.log(response);
        this.todoItems = this.todoItems.filter((i) => i.id != item.id);
        //this.todoItems.push(response.data);
      });
      this.todoItems = this.todoItems.filter((i) => i.id != item.id);
    },
    saveTodo(data) {
      console.log("save-todo", data);
    },
    test(data) {
      console.log("test-todo", data);
    },
    addTodo(item) {
      const obj = {
        id: new Date(),
        text: item,
      };
      console.log(item);

      axios.post("http://localhost:3000/todos", obj).then((response) => {
        console.log(response);
        this.todoItems.push(response.data);
      });
    },
  },
  data() {
    return {
      todoItems: [],
    };
  },
};
</script>

<style></style>
