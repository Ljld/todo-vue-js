<template>
  <header>
    <h1>ToDo VueJS</h1>
  </header>
  
  <ToDoList/>
</template>

<script>
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'App',
  components: {
    ToDoList
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /*background-color: #f6f6f6;*/
  background-image: linear-gradient(to bottom right, #8d39aa, #6646f1);
  height: 100vh;
}

header {
  /*background-image: linear-gradient(to bottom right, #8d39aa, #6646f1);*/
  height: 5em;
  display: flex;
  justify-content: center;
  margin-bottom: 3em;
}

h1 {
  color: white;
  margin: auto;
}

.todo {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}
</style>
