<template>
  <div>
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'TodoHeader',
  props: {
    msg: {
      type: String,
      required:true
    }
  }
}
</script>

<style scoped>

</style>
