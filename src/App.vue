<template>
  <div class="header">
    <h1>Todo Application</h1>
  </div>
  <form action="" @submit.prevent="addTodo" >
    <input type="text" v-model="todoText">
    <input type="button" value="Add">
  </form>
  <div class="todo__thread">
    <div class="todo" v-for="todo in todos" :key="todo.id">
      <h3>{{ todo.todo }}</h3>
      <button
      @click="removeTodo(todo.id)"
      >Remove Item</button>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      todoText: '',
      todos:[{id:1, todo:'First Todo'}]
    }
},
methods:{
  addTodo(){
    this.todos.push({id:Math.random(), todo: this.todoText})
    this.todoText = ''
  },
  removeTodo(id){
    this.todos = this.todos.filter((item) => item.id !== id);
  }
}
};
</script>

<style>
.todo{
  display: flex;
  background-color: blanchedalmond;
  padding: 15px;
  margin: 10px;
  border-radius: 25px;
  justify-content: space-between;
}
</style>