<template>
  <div id="app">
    <RandomQuotes :title="titleQuotes" />
    <ToDoList :title="titleToDo"/>
  </div>
</template>

<script>

import ToDoList from './components/ToDoList.vue';
import RandomQuotes from './components/RandomQuotes.vue';

export default {
  data() {
    return {
      titleToDo: 'To Do List',
      titleQuotes: 'Famous Quotes'
    }
  },
  name: 'App',
  components: {
    ToDoList,
    RandomQuotes
  }
}

</script>

<style>

</style>
