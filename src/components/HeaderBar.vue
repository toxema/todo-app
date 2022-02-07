<template>
  <div class="">
    <span class="text-gray">{{ msg }}</span>
 
  </div>
</template>

<script>
export default {
  name: 'HeaderBar',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
