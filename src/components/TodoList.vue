<template>
    <ul class="list">
        <ListItem v-for="item of items" v-bind:item="item" v-bind:key="item.id"/>
    </ul>
</template>

<script>
import ListItem from "@/components/ListItem";

export default {
  name: "TodoList",
  components: {
    ListItem
  },
  data(){
    return {
      items:[
        {id:'1', text:'Сходить в магазин', isDone:false},
        {id:'2', text:'Купить пиво', isDone:false},
        {id:'3', text:'Убраться дома', isDone:false}
      ]
    }
  }
}
</script>

<style scoped>
  .list{
      list-style: none;
      padding: 0;
  }
</style>