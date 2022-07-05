<template>
  <div class="container">
    <form @submit.prevent="submit">
      <label for="taskName">Task name: </label>
      <input type="text" id="taskName" v-model="taskName" />
      <button type="submit">Add</button>
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid";
import axios from "axios";
export default {
  data() {
    return {
      taskName: "",
    };
  },
  methods: {
    submit() {
      console.log(this.taskName);
      axios
        .post("http://localhost:3000/todoList", {
          name: this.taskName,
          done: false,
          id: uuidv4(),
        })
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
  watch: {},
};
</script>

<style>
</style>