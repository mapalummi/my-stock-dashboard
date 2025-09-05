<template>
  <div class="dashboard-container">
    <BaseCard title="Revenues Q1 2024" class="top-row-card">
      <div class="revenue-tickers">
        <RevenueCard variant="square" symbol="$AAPL" />
        <RevenueCard variant="square" symbol="$META" />
        <RevenueCard variant="square" symbol="$MSFT" />
        <RevenueCard variant="square" symbol="$GOOG" />
        <RevenueCard variant="square" symbol="$AMZN" />
        <RevenueCard variant="square" symbol="$TSLA" />
      </div>
    </BaseCard>

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
import RevenueCard from "@/components/RevenueCard.vue";
import RevenueBreakdownCard from "./components/RevenueBreakdownCard.vue";
import NetIncomeCard from "./components/NetIncomeCard.vue";
import GrossMarginCard from "./components/GrossMarginCard.vue";
import RevenueGrowthCard from "./components/RevenueGrowthCard.vue";

export default {
  name: "App",
  components: {
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

.revenue-tickers {
  display: flex;
  gap: 16px;
}

.revenue-tickers > .card {
  flex: 1;
  min-width: 150px; /* Optional: Setze eine Mindestbreite, damit sie nicht zu klein werden */
}

/* Mittlere Reihe: 70/30 Aufteilung */
.middle-row {
  display: flex;
  gap: 16px;
}

.middle-row .revenue-history-card {
  flex: 7; /* Karte nimmt 70% der verfügbaren Breite ein */
}

.middle-row .magnificent-seven-card {
  flex: 3; /* Karte nimmt 30% der verfügbaren Breite ein */
}

.bottom-row {
  display: flex;
  gap: 16px;
}

.bottom-row .net-income-card {
  flex: 4; /* Beispiel: Die ersten beiden Karten nehmen zusammen so viel Platz ein wie die 70% der mittleren Reihe */
}

.bottom-row .gross-margin-card {
  flex: 3;
}

.bottom-row .revenue-growth-card {
  flex: 3; /* Diese Karte nimmt so viel Platz ein wie die 30% der mittleren Reihe */
}
</style>
