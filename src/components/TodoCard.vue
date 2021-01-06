<template>
  <div class="todo-list">
    <transition name="fade">
      <div class="todo-card">
        <p @click="$event.target.classList.toggle('completeTask')">
          {{ text }}
        </p>
      </div>
    </transition>
  </div>
</template>

<script>
// See our components in the codebase for examples of
// defining components, importing and using components
export default {
  name: "TodoCard",
  components: {},
  // Prop types in vue docs on google
  props: ["text"],
  data() {
    return {};
  },
  methods: {},
};
</script>

<style scoped>
.todo-list {
  display: flex;
  justify-content: space-evenly;
}

.todo-card {
  margin: 30px auto;
  padding: 75px 0;
  width: 200px;
  height: 90px;
  background-image: linear-gradient(#DD2476, #FF512F);
  border-radius: 7px;
  text-align: center;
  color: #fff;
  font-weight: 600;
  font-size: 20px;
  box-shadow: 9px 10px 15px -5px rgba(65, 65, 65, 0.5);
  animation: fadein 0.5s;
  cursor: pointer;
}

.deleteButton {
  font-size: 10px;
  margin: 0 0.5em;
  border-radius: 2em;
  padding: 0.75em 1.5em;
  cursor: pointer;
  background: none;
  border: 1px solid;
  letter-spacing: 1px;
  color: white;
  transition: 250ms ease-out;
}

.deleteButton:hover {
  color: #DD2476;
  background-color: white;
}

.completeTask {
  text-decoration: line-through;
}

@keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
