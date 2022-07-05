<template>
  <div class="container">
    <h1>Task list</h1>
    <div class="item" v-for="(task, index) in tasks" :key="index">
      <div>
        <input type="checkbox" name="" :id="index" v-model="task.done" />
        <label :for="index" :class="task.done ? 'completed' : ''">{{
          task.name
        }}</label>
      </div>
      <button @click="deleteTask(task.id)">Delete</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: { tasks: Array },
  data() {
    return {
      everthingIsReady: false,
    };
  },
  methods: {
    deleteTask(id) {
      axios.delete(`http://localhost:3000/todoList/${id}`).then((response) => {
        console.log(response);
      });
      this.$router.go("/");
    },
  },
  watch: {
    tasks() {
      // console.log("re-render");
    },
  },
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  text-align: left;
  padding: 10px 40px;
  width: 100%;
  align-items: center;
}
.item {
  display: flex;
  width: 40%;
  justify-content: space-between;
  margin-bottom: 4px;
}
.item button {
  float: right;
}
.loading {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  height: calc(100vh - 400px);
  font-size: 60px;
  animation: rotating 2s linear infinite;
  color: #42b983;
}
.completed {
  text-decoration: line-through;
  color: #999;
}
@keyframes rotating /* Safari and Chrome */ {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>