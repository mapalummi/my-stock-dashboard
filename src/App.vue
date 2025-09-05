<template>
  <BaseCard title="Mein Dashboard">
    <p>Willkommen zu meinem Stock Dashboard!</p>
  </BaseCard>

  
<div class="cards-container">
  <RevenueCard variant="square" symbol="$AAPL" />
  <RevenueBreakdownCard variant="square" :tickers="['$AAPL', '$MSFT', '$NVDA']" />
</div>
  

</template>

<script>
import BaseCard from "./components/Basecard.vue";
import { stockService } from "@/services/stockService";
import RevenueCard from "@/components/RevenueCard.vue";
import RevenueBreakdownCard from "./components/RevenueBreakdownCard.vue";

export default {
  name: "App",
  components: {
    BaseCard,
    RevenueCard,
    RevenueBreakdownCard,
  },
  async created() {
    this.data = await stockService.getRevenue("$AAPL");
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
.cards-container {
  display: flex;
  gap: 16px;
  margin-top: 1rem;
}
/* .cards-container .card {
  width: 300px;
  flex: none;
} */
 
 /* Für unterschiedliche Breiten */
.cards-container .card:first-child {
  flex: 2; /* Doppelt so breit */
}
.cards-container .card:last-child {
  flex: 1;
}
</style>
