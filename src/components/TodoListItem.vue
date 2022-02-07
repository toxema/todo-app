<template>
  <div>
    <div @click="toggle" class="todo p-1 mt-1 bg-light d-flex justify-content-between align-items-center">
      <img src="@/assets/go-next.png" v-if="!expand" />
      <img src="@/assets/go-down.png" v-if="expand" />
      <span class="mx-2 flex-fill"> {{ item.text }} </span>
      <button class="btn btn-dark" @click="deleteItem">X</button>
    </div>
    <todo-item-detail v-if="expand && !deleteConfirm" :item="item" />
    <item-delete-dialog v-if="deleteConfirm" @delete-item="$emit('delete-item', item)" @delete-cancel="cancelDelete" />
  </div>
</template>

<script>
import TodoItemDetail from "@/components/TodoItemDetail.vue";
import ItemDeleteDialog from "@/components/ItemDeleteDialog.vue";

export default {
  components: {
    TodoItemDetail,
    ItemDeleteDialog,
  },
  name: "TodoListItem",
  props: ["item"],
  data() {
    return {
      expand: false,
      deleteConfirm: false,
      showDeletePopup: false,
    };
  },
  methods: {
    deleteItem() {
      if (this.showDeletePopup) {
        this.deleteConfirm = !this.deleteConfirm;
      } else {
        this.$emit("delete-item", this.item);
      }
    },
    toggle() {
      this.expand = !this.expand;
      console.log("Expand op");
    },
    cancelDelete() {
      this.expand = false;
      this.deleteConfirm = false;
    },
  },
};
</script>

<style scoped>
.todo:hover {
  background: aquamarine;
  cursor: pointer;
}
</style>
