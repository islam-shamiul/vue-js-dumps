<template>
  <div id="app">
    <appHeader></appHeader>
    <AddTodo v-on:add-todo="addTodo"></AddTodo>
    <TodoList v-bind:todos="todos" v-on:del-todo="deletTodo"></TodoList>
  </div>
</template>

<script>
import appHeader from "./components/layout/appHeader.vue";
import TodoList from "./components/TodosList.vue";
import AddTodo from "./components/AddTodo.vue";

export default {
  name: "App",
  components: {
    TodoList,
    appHeader,
    AddTodo,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Todo One",
          completed: false,
        },
        {
          id: 2,
          title: "Todo Two",
          completed: false,
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false,
        },
      ],
    };
  },
  methods: {
    deletTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
