<template>
  <div class="dialog">
    <div class="m-3 shadow p-3">
      <span class="h2"> Todo itemi silmek istediğinize emin misiniz?</span>
      <br /><br />
      <button class="btn btn-danger mx-2" @click="onOk">Delete</button>
      <button class="btn btn-success" @click="onCancel">Vazgeç</button>
    </div>
  </div>
</template>
<script>
export default {
  inject: ["apim"],
  methods: {
    onOk() {
      this.$emit("delete-item");
      this.apim.test("on Ok");
    },
    onCancel() {
      this.$emit("delete-cancel");
      this.apim.saveTodo("on cancel");
    },
  },
};
</script>
