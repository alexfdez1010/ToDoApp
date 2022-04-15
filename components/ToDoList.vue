<template>
  <h1 id="title">{{title}}</h1>
  <form id="add-task-container" @submit.prevent="addTodo">
    <input type="text" v-model="todoName" placeholder="Name" />
    <input type="number" v-model="todoTime" placeholder="Time (hours)" />
    <button class="add" type="submit">Añadir</button>
  </form>
  <div id="task-container">
    <div class="task" v-for="todo in todos" :key="todo.id">
      <p>Name: {{todo.name}}</p>
      <p>Number of hours required: {{todo.time}}</p>
      <p>Completed: <input type="checkbox" v-model="todo.completed" /></p>
      <button class="remove" @click="removeTodo(todo)">X</button>
    </div>
  </div>
</template>

<script>

import json from '../json/data.json'

export default {
  name: 'ToDoList',
  data() {
    return {
      todos : [...json],
      id: 12345,
      todoName: '',
      todoTime: 0,
    }
  },
  props: {
    title: {
      type: String,
      required: true
    }
  },
  methods: {
    addTodo(){
        this.todos.push({id: this.id++, name: this.todoName, time: this.todoTime, completed: false});
        this.todoName = '';
        this.todoTime = 0;
    },
    removeTodo(todo){
        this.todos = this.todos.filter(t => t.id !== todo.id);
    }
  }
}
</script>

<style scoped>
#title{
  font-size: 2em;
  text-align: center;
}
#add-task-container{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  background: black;
  width: 60%;
  padding: 20px 0;
  margin: 20px auto;
  border-radius: 5px;
}
#add-task-container>input, #add-task-container>button{
  margin: 0 10px;
  width: 25%;
  height: 100%;
}

#task-container{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  flex-basis: 20%;
}

.task{
  width: 200px;
  height: 0;
  padding: 100px 0;
  background: black;
  margin: 2.5%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border-radius: 5%;
  color: white;
  position: relative;
}

.task>p, .task>input{
  font-size: 14px;
}

.add{
  background: #00b300;
  margin: 0.4%;
  width: 15%;
  border-radius: 0.7%;
  border: 1px solid black;
  color: white;
  font-weight: bold;
}

.remove{
  position: absolute;
  top: 2.5%;
  right: 2.5%;
  background: #ff0000;
  width: 10%;
  height: 0;
  padding: 5% 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border-radius: 20%;
  border: 1px solid black;
  cursor: pointer;
}

</style>