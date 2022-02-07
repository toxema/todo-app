<template>
  <div class="bg-gray p-2 m-2">
    Expanded div
    <hr />
    <br />
    <img src="@/assets/logo.png" width="100" height="100" />
    <button class="btn btn-success">Edit</button>
    <hr />
    <i>{{ item.id.toLocaleString("tr-TR") }}</i>
  </div>
</template>
<script>
export default {
  props: ["item"],
  data() {
    return {};
  },
};
</script>
