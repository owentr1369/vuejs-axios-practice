<template>
  <div class="home">
    <currency-component :info="info"></currency-component>
  </div>
</template>

<script>
import axios from "axios";

import CurrencyComponent from "@/components/CurrencyComponent.vue";

export default {
  name: "HomeView",
  components: { CurrencyComponent },
  data() {
    return {
      info: [],
    };
  },
  created() {
    axios
      .get("https://api.coindesk.com/v1/bpi/currentprice.json")
      .then((response) => {
        this.info = response.data;
        console.log(this.info);
      });
  },
};
</script>
