<template>
  <div class="container">
    <h1>Task list</h1>
    <div class="item" v-for="(task, index) in tasks" :key="index">
      <input type="checkbox" name="" :id="index" :checked="task.done" />
      <label :for="index">{{ task.name }}</label>
    </div>
  </div>
</template>

<script>
export default {
  props: { tasks: Array },
  data() {
    return {
      everthingIsReady: false,
    };
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
  text-align: left;
  margin-left: 40px;
  width: 100%;
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
@keyframes rotating /* Safari and Chrome */ {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>