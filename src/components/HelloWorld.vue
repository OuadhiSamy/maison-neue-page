<template>
  <h1>{{ msg }}</h1>
</template>

<script>
  export default {
    component: 'hello-world',
    data: () => {
      return {
        message: 'Hello',
      }
    }
  } 
</script>

<style scoped>
a {
  color: #42b983;
}
</style>
