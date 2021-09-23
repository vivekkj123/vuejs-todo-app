<template>
  <div class="header">
    <p class="notepadIcon">🗒</p>
    <h1>Todo Application</h1>
  </div>
  <form action="" @submit.prevent="addTodo">
    <input class="inputBox" required type="text" v-model="todoText" />
    <input class="addBtn" type="submit" value="👉" />
  </form>
  <div class="todo__thread">
    <div class="todo" v-for="todo in todos" :key="todo.id">
      <input @click="markAsCompleted(todo)" type="checkbox" name="" id="" />
      <h3
        v-bind:style="[
          todo.completed
            ? {
                textDecoration: line-through,
              }
            : {  },
        ]"
      >
        {{ todo.todo }}
      </h3>
      <button @click="removeTodo(todo.id)" class="removebtn">🗑</button>
    </div>
  </div>
  <div class="footer">Made By Vivek with ❤️ for learning Vue.Js</div>
</template>

<script>
export default {
  data() {
    return {
      todoText: "",
      todos: [{ id: 1, todo: "First Todo" }],
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: Math.random(),
        todo: this.todoText,
        completed: false,
      });
      this.todoText = "";
    },
    removeTodo(id) {
      this.todos = this.todos.filter((item) => item.id !== id);
    },
    markAsCompleted(todo) {
      let selectedTodo = this.todos.filter((item) => item.id === todo.id);
      if (selectedTodo.completed) {
        selectedTodo.completed = false;
      } else {
        selectedTodo.completed = true;
      }
    },
  },
};
</script>

<style>
html {
  font-family: "Sora", sans-serif;
  background-color: #040631;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
}
.header,
.footer {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}
.todo {
  display: flex;
  background-color: #ffff;
  color: black;
  padding: 15px;
  margin: 10px;
  border-radius: 15px;
  width: 450px;
  justify-content: space-between;
}
form {
  text-align: center;
  margin: 20px;
}
.inputBox {
  height: 40px;
  width: 380px;
  border-radius: 15px;
}
.notepadIcon {
  font-size: 50px;
  margin: 0;
}
.addBtn {
  background: none;
  color: inherit;
  border: none;
  font-size: 30px;
  cursor: pointer;
}
.removebtn {
  background: none;
  color: inherit;
  border: none;
  font-size: 30px;
  cursor: pointer;
}
.strike {
}
</style>