<template>
  <div id="app" class="container">
    <h1 class="mt-5 mb-4">Todo App</h1>
    <todo-list :todos="todos" @addTodo="addTodo" @deleteTodo="deleteTodo" />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    TodoList,
  },
  data() {
    return {
      todos: [
        { id: 1, text: 'Buy groceries', completed: false },
        { id: 2, text: 'Go for a run', completed: true },
      ],
    };
  },
  methods: {
    addTodo(newTodoText) {
      const newTodo = { id: this.todos.length + 1, text: newTodoText, completed: false };
      this.todos.push(newTodo);
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId);
    },
    
  },
};
</script>

<style>
#app {
  
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>