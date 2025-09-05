<template>
  <div class="dashboard-container">
    <RevenueTickersCard class="top-row-card" />

    <div class="middle-row">
      <RevenueCard variant="square" symbol="$AAPL" class="revenue-history-card" />
      <RevenueBreakdownCard variant="square" :tickers="['$AAPL', '$MSFT', '$NVDA']" class="magnificent-seven-card" />
    </div>

    <div class="bottom-row">
      <NetIncomeCard variant="square" class="net-income-card" />
      <GrossMarginCard variant="square" class="gross-margin-card" />
      <RevenueGrowthCard variant="square" class="revenue-growth-card" />
    </div>
  </div>
</template>

<script>
import { stockService } from "@/services/stockService";
import RevenueTickersCard from "./components/RevenueTickersCard.vue";
import RevenueCard from "@/components/RevenueCard.vue";
import RevenueBreakdownCard from "./components/RevenueBreakdownCard.vue";
import NetIncomeCard from "./components/NetIncomeCard.vue";
import GrossMarginCard from "./components/GrossMarginCard.vue";
import RevenueGrowthCard from "./components/RevenueGrowthCard.vue";

export default {
  name: "App",
  components: {
    RevenueTickersCard,
    RevenueCard,
    RevenueBreakdownCard,
    NetIncomeCard,
    GrossMarginCard,
    RevenueGrowthCard,
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
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.dashboard-container {
  display: flex;
  flex-direction: column;
  gap: 16px;
  width: 100%;
}

.top-row-card {
  width: 100%;
}


/* Middle row: 70/30 split */
.middle-row {
  display: flex;
  gap: 16px;
}

.middle-row .revenue-history-card {
  flex: 7; /* Card takes 70% of available width */
}

.middle-row .magnificent-seven-card {
  flex: 3; /* Card takes 30% of available width */
}

.bottom-row {
  display: flex;
  gap: 16px;
}

.bottom-row .net-income-card {
  flex: 4; /* Example: First two cards take as much space as 70% of middle row */
}

.bottom-row .gross-margin-card {
  flex: 3;
}

.bottom-row .revenue-growth-card {
  flex: 3; /* This card takes as much space as 30% of middle row */
}
</style>
