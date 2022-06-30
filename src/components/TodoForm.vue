<template>
  <form v-on:submit.prevent="onSubmit">
    <input type="text" v-model="title" placeholder="Type text here">
    <button type="submit">Add</button>
  </form>
</template>

<script>
export default {
  name: "TodoForm",
  data(){
    return{
      title:''
    }
  },
  methods:{
    onSubmit(){
        if (this.title.trim()) {
          const newItem = {id: Date.now(), text: this.title, isDone: false}

          this.$emit('add-item', newItem)

          this.title = ''
        }
    }
  }
}
</script>

<style scoped>

</style>