<template>
    <ul class="list">
        <ListItem v-for="item of items" v-bind:item="item" v-on:remove-item="removeItem"
                  @toogle-value="toogleValue"
                  v-bind:key="item.id"/>
    </ul>
</template>

<script>
import ListItem from "@/components/ListItem";

export default {
  name: "TodoList",
  props:{
    items: Array
  },
  components: {
    ListItem
  },
  methods:{
    removeItem(id){
      this.$emit('remove-item',id)
    },
    toogleValue(id){
      this.$emit('toogle-value',id)
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