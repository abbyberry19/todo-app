<template>
  <div class="wrapper">
    <h1>{{ message }}</h1>
    <h2>TO-DO:</h2>
    <br />
    <form @submit.prevent="onSubmitTodo" class="task-input">
      <input
        type="text"
        v-model="newTodoText"
        placeholder="What next?"
        class="text-box"
      />
      <button class="btn" type="submit">Save TODO</button>
    </form>
    <div class="container" v-on:click="deleteTodo(id)">
      <TodoCard v-for="todo in savedTodos" :key="todo.id" :text="todo.text" />
    </div>
  </div>
</template>

<script>
import TodoCard from "./TodoCard.vue";

export default {
  name: "HelloWorld",
  components: {
    TodoCard,
  },
  props: {},
  data() {
    return {
      message: "A Neat TODO App",
      newTodoText: "",
      // savedTodos should contain objects with at least id and text properties
      savedTodos: [
        {
          id: 1,
          text: "Take the bins out",
        },
      ],
    };
  },
  methods: {
    onSubmitTodo() {
      if (this.newTodoText) {
        const todoId = this.savedTodos.length + 1;
        this.savedTodos.push({
          id: todoId,
          text: this.newTodoText,
        });
        this.newTodoText = "";
      }
    },
    deleteTodo(id) {
      this.savedTodos.splice(id, 1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Gochi+Hand&family=Oswald&display=swap");

h1 {
  font-family: "Gochi Hand", cursive;
}

h2 {
  font-family: "Oswald", sans-serif;
}

h3 {
  font-family: "Oswald", sans-serif;
  margin: 40px 0 0;
}

.wrapper {
  min-height: 50vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  border-radius: 1em;
  background: #fff;
  overflow: hidden;
  box-shadow: 0 0 5px rgba(25, 25, 25, 0.25);
}

.container {
  z-index: 0;
  width: 100%;
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
}

.text-box {
  font-size: 14px;
  margin: 0 0.5em;
  border-radius: 2em;
  padding: 0.75em 1.5em;
  border: 1px solid rgb(209, 209, 209);
  margin-left: auto;
  margin-right: auto;
  width: 200px;
}

.btn {
  font-size: 14px;
  margin: 0 0.5em;
  border-radius: 2em;
  padding: 0.75em 1.5em;
  cursor: pointer;
  background: none;
  border: 1px solid;
  letter-spacing: 1px;
  color: #DD2476;
  transition: 250ms ease-out;
}

.btn:hover {
  color: #fff;
  background-color: #DD2476;
}
</style>
