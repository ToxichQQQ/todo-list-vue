<template>
  <li class="list-item">
    <input type="checkbox" v-bind:checked="item.isDone" v-on:change="$emit('toogle-value',item.id)">
    <span class="text" v-bind:class="{done: item.isDone }">{{item.text}}</span>
    <button v-on:click="$emit('remove-item',item.id)">&times;</button>
    </li>
</template>

<script>
export default {
  name: "ListItem",
  props:{
    item: Object
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

  .text{
    text-wrap: normal;
  }

  .done{
    text-decoration: line-through;
    color: grey;
  }

</style>