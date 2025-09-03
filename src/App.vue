<template>
  <BaseCard title="Mein Dashboard">
    <p>Willkommen zu meinem Stock Dashboard!</p>
  </BaseCard>
</template>

<script>
import BaseCard from "./components/Card.vue";
import { stockService } from "@/services/stockService";

export default {
  name: "App",
  components: {
    BaseCard,
  },
  async created() {
    this.data = await stockService.fetchData("$AAPL");
    console.log("Loaded data", this.data);
  },
};
</script>

<style>
body {
  margin: 0;
}
#app {
  width: 100vw;
  min-height: 100vh;
  padding: 100px;
  background: radial-gradient(71.11% 100% at 50% 0%, #020204 14.6%, #011f35 100%);
  box-sizing: border-box;
}
</style>
