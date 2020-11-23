<template>
  <div id="app">
    <h1>ToDo's</h1>
    <form v-on:submit.prevent="saveNewTodo">
      <label for="new-todo"></label>
      <input id="new-todo" type="text" placeholder="Add new todo to list" v-model="newTodo"/>
      <input type="radio" id="high" name="priority" value="priority">
      <label for="high">High</label>
      <input type="radio" id="low" name="priority" value="priority">
      <label for="low">Low</label>
      <input type="submit" value="Save new todo">
    </form>

    <ul>
      <li v-for="(todo, index) in todos" v-bind:key="index">{{todo.task}}</li>
    </ul>

  </div>
</template>

<script>

export default {
  data(){
    return {
      todos: [{task: "Walk the dog"},
              {task: "Wash the dishes"}, 
              {task: "Water the plants"}
              ],
              // couldn't get it to work without it being an object - todos: ["Walk the dog", "Wash the dishes", "Water the plants"],
      newTodo: ""
    }
  },
  methods: {
    saveNewTodo: function(){
      this.todos.push({
        task: this.newTodo,
        })
      this.newTodo = "";
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
