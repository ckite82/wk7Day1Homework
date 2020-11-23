<template>
  <div id="app">
    <h1>ToDo's</h1>
    <form v-on:submit.prevent="saveNewTodo">
      <label for="new-todo"></label>
      <input id="new-todo" type="text" placeholder="Add new todo to list" v-model="newTodo"/>
      <input type="radio" id="high" name="priority" value="High" v-model="newPriority"/>
      <label for="high">High</label>
      <input type="radio" id="low" name="priority" value="Low" v-model="newPriority"/>
      <label for="low">Low</label>
      <input type="submit" value="Save new todo"/>
    </form>

    <ul>
      <li v-for="(todo, index) in todos" v-bind:key="index" v-bind:class="todo.priority ? 'high':'low'">
        <span>{{todo.task}}</span>
        <span v-if>{{todo.priority}}</span>
        </li>
    </ul>

  </div>
</template>

<script>

export default {
  data(){
    return {
      todos: [{task: "Walk the dog", priority: "High"},
              {task: "Wash the dishes", priority: "Low"}, 
              {task: "Water the plants", priority: "High"},
              ],
              // couldn't get it to work without it being an object - todos: ["Walk the dog", "Wash the dishes", "Water the plants"],
      newTodo: ""
    }
  },
  methods: {
    saveNewTodo: function(){
      this.todos.push({
        task: this.newTodo,
        priority: this.newPriority,
        })
      this.newTodo = "";
      this.newPriority = "";
    }
  }
}
</script>

<style>
#app {
  font-family: 'Lato', sans-serif;
  width: 60%;
  margin: 0 auto;
  /* -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}

h1 {
  font-size: 3rem;
  font-style: bold;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

li {
  margin: 20px 0;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}

li span {
  padding: 8px;
}

/* li button {
  background: #f2360c;
  color: #fff;
  border: none;
  padding: 10px;
  cursor: pointer;
} */

/* li.purchased {
  border: 2px solid #1a681e;
  color: #1a681e;
}

li.not-purchased {
  border: 2px solid #f2360c;
} */

input[type="text"] {
  padding: 10px;
  width: 50%;
  margin: 5px;
}

button, input[type="submit"] {
  padding: 10px;
  margin: 10px;
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
}

</style>