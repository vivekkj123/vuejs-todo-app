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
      <input type="checkbox" class="" name="" id="" />
      <label
        class="todo"
      >
        {{ todo.todo }}
      </label>
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
      todos: [{ id: 1, todo: "First Todo"}],
      textDecoration: 'lineThrough',
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: Math.random(),
        todo: this.todoText,
      });
      this.todoText = "";
    },
    removeTodo(id) {
      this.todos = this.todos.filter((item) => item.id !== id);
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
input[type=checkbox]:checked + label.todo{
  text-decoration: line-through;
}
</style>