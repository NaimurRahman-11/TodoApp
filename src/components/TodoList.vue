<template>
  <div>
    <div class="mb-3">
      <input v-model="newTodoText" @keyup.enter="addTodo" class="form-control" placeholder="Add a new todo" />
    </div>
    <ul class="list-group">
      <li class="list-group-item" v-for="todo in todos" :key="todo.id">
        <todo-item :todo="todo" @deleteTodo="deleteTodo" />
      </li>
    </ul>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
  name: 'TodoList',
  components: {
    TodoItem,
  },
  props: ['todos'],
  data() {
    return {
      newTodoText: '',
    };
  },
  methods: {
    addTodo() {
      if (this.newTodoText.trim() === '') return;
      this.$emit('addTodo', this.newTodoText);
      this.newTodoText = '';
    },
    deleteTodo(todoId) {
      this.$emit('deleteTodo', todoId);
    },
    
  },
};
</script>