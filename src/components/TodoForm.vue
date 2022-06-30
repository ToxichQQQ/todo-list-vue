<template>
  <form v-on:submit.prevent="onSubmit" class="form">
    <input class="input" type="text" v-model="title" placeholder="Type text here">
    <button class="button" type="submit">Add</button>
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
  .input{
    width: 250px;
    height: 16px;
    border-radius: 10px;
    border: 1px solid grey;
    padding: 5px;
  }

  .button{
    margin-right: 10px;
    border: 1px solid grey;
    padding: 5px 7px;
    border-bottom-right-radius: 10px;
    border-top-right-radius: 10px;
    transform: translateX(-40px);
  }

</style>