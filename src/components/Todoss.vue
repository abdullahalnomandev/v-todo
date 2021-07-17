<template>
  <div>
    <h3>TOOODOS</h3>


    <div class="legend">
      <span>Double click to mark as complete</span>
    </div>

    <span>
      <span class="incomplete-box"> </span>= Incomplete
    </span>

    
    <span>
      <span class="complete-box"> </span>= Completed
    </span>

    <div class="todoss">
      <div 
      @dblclick="onDbClick(todo)" 
      v-for="todos in allTodos" 
      :key="todos.id" 
      class="todo"
      v-bind:class="{'is-complete':todos.completed}"
      >
        <p>{{todos.id}}</p>
        <h3>{{ todos.title }}</h3>
        <font-awesome-icon :icon="deleteIcom" class="icon" 
        @click="deleteTodo(todos.id)"
        />
      </div>
    </div>
    <h3 v-if="allTodos.length===0" class="text-center ">Loading...</h3>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faTrash } from "@fortawesome/free-solid-svg-icons";
import { mapGetters, mapActions } from "vuex";
export default {
  name: "Todoss",
  data() {
    return {
      deleteIcom: faTrash,
    };
  },
  methods: {
    ...mapActions(["fetchTodos","deleteTodo","updateTodo"]),
  },
  computed: mapGetters(["allTodos"]),

    onDbClick(todo){
      const updTodo={
        id:todo.id,
        title:todo.title,
        completed: !todo.completed
      }
      this.updateTodo(updTodo)
    },
  created() {
    this.fetchTodos();
  },
  components: {
    FontAwesomeIcon,
  },
};
</script>

<style scoped>
.todoss {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}
.todo {
  border: 1px solid #ccc;
  background: #09f088;
  padding: 1rem;
  border-radius: 5px;
  text-align: center;
  position: relative;
  cursor: pointer;
}
.icon{
  position: absolute;
  bottom: 10px;
  right:10px;
  color:red;
  cursor: pointer;
}

.legend{
  display: flex;
  justify-content:space-around;
  margin-bottom: 1rem;
}

.complete-box{
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #35495e;
}
.incomplete-box{
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #09f088;
}

@media (max-width:500px){
  .todoss{
    grid-template-columns: 1fr;
  }
}

.is-complete{
  background: #35495e;
  color: white;
}
</style>
