<template >
  <div class="home">
    <task-list v-if="everthingIsReady" :tasks="tasks"></task-list>
    <div class="loading" v-else>
      <i class="fa-solid fa-spinner"></i>
    </div>
  </div>
</template>

<script>
import axios from "axios";

import TaskList from "@/components/TaskList.vue";

export default {
  name: "HomeView",
  data() {
    return {
      everthingIsReady: false,
      tasks: [],
    };
  },
  components: { TaskList },
  created() {
    axios.get("http://localhost:3000/todoList").then((response) => {
      this.tasks = response.data;
      console.log(this.tasks);
    });
  },
  watch: {
    tasks() {
      if (this.tasks.length > 0) {
        this.everthingIsReady = true;
      }
    },
  },
};
</script>
