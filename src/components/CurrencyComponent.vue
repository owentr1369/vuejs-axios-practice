<template>
  <div class="container">
    <h1>{{ info.disclaimer }}</h1>
    <div class="item" v-for="(item, index) in info.bpi" :key="index">
      <h2>Currency: {{ item.description }} - {{ item.code }}</h2>
      <h3>Rate: {{ item.rate }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  props: { info: Object },
};
</script>

<style>
.container {
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
  text-align: left;
  margin-left: 40px;
}
</style>