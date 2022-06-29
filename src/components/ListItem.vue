<template>
  <li class="list-item">
    <input type="checkbox">
    <span>{{item.text}}</span>
    <button>&times;</button>
    </li>
</template>

<script>
export default {
  name: "ListItem",
  props:{
    item:{
      type:Object,
      required:true
    }
  }
}
</script>

<style scoped>
  .list-item{
    border:1px solid grey;
    border-radius: 10px;
    padding: 10px;
    margin-bottom: 10px;

    display: flex;
    justify-content: space-between;
  }
</style>