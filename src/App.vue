<template>
  <div id="app">
    <Header></Header>
    <Input></Input>
    <List></List>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Input from './components/Input.vue'
import List from './components/List.vue'

export default {
  name: 'App',
  components: {
    Header,
    Input,
    List,
  }
}
</script>

<style scoped>
  body {
  font-family: 'Ubuntu', sans-serif;
  font-weight: 300;
}
  
</style>

