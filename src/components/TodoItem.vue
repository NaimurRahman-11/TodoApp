<template>
  <div class="form-check">
   
    <div class="d-flex justify-content-between align-items-center"> 
         <input type="checkbox" class="form-check-input" v-model="todo.completed" />
        <label :class="{'form-check-label': true, completed: todo.completed }">{{ todo.text }}</label>
    <button class="btn btn-danger" @click="deleteTodo">Delete</button>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  methods: {
    deleteTodo() {
      this.$emit('deleteTodo', this.todo.id);
    },
    
  },
};
</script>

<style>
.completed {
  text-decoration: line-through;
}
</style>
