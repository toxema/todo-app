<template>
  <div class="">
    <div class="mx-2">
      <todo-list-item class=" "
       v-for="item in datam" 
       :key="item.id"
       :item="item"
       @delete-item=" $emit('delete-item',$event)" />
         
         <span class=  " my-3 font-sm text-dark">{{datam.length}} adet doto item var.</span>
       
    </div>
  </div>
</template>

<script>
import TodoListItem from "@/components/TodoListItem.vue";
 
export default {
  components: {
    TodoListItem,
  },
   props:["datam"]

  ,
  data() {
    return {
    } 
  },
  methods: {
    
  },
};
</script>

 