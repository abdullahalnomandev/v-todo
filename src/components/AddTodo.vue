<template>
  <div>
    <h3>Add Todo</h3>
    <div class="add ">
      <form @submit="onSubmit" action="">
        <div class="text-center">
          <input
            type="text"
            v-model="title"
            placeholder="Add Todo...."
            class="form-control w-50 d-inline-block "
          />
          <input
            class="btn-success px-3 py-2 rounded ms-3"
            type="submit"
            value="Submit"
          />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "AddTodo",
  data() {
    return {
      title:'',
    };
  },
  methods: {
    ...mapActions(['addTodo']),
    onSubmit(e){
        e.preventDefault();
        this.addTodo(this.title)
        this.title=''
    }
  },
};
</script>

<style lang="scss" scoped></style>
