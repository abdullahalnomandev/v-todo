<template>
  <div class="app">
    <div class="container pt-5">
      <Add-todo />
      <Filter-todos />
      <Todoss />
    </div>
  </div>
</template>

<script>
import AddTodo from "./components/AddTodo.vue";
import FilterTodos from './components/FilterTodos.vue';
import Todoss from "./components/Todoss.vue";
export default {
  components: { Todoss, AddTodo, FilterTodos },
  name: "App",
};
</script>

<style scoped>
.app {
  background-color: #7f9c9c;
  min-height: 100vh;
}
</style>
