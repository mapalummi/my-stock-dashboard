<template>
  <div class="revenue-tickers-card">
    <div class="card-content">
      <div class="revenue-tickers">
        <RevenueCard v-for="symbol in symbols" :key="symbol" variant="square" :symbol="symbol" />
      </div>
    </div>
  </div>
</template>

<script>
import RevenueCard from "./RevenueCard.vue";

export default {
  name: "RevenueTickersCard",
  components: {
    RevenueCard,
  },
  props: {
    title: {
      type: String,
      default: "Revenues Q1 2024",
    },
    symbols: {
      type: Array,
      default: () => ["$AAPL", "$META", "$MSFT", "$GOOG", "$AMZN", "$TSLA"],
    },
  },
};
</script>

<style scoped>
.revenue-tickers-card {
  background: #023a6233;
  border-radius: 16px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  padding: 24px 32px;
  margin: 0;
  display: flex;
  flex-direction: column;
  width: 100%;
}

.card-content {
  flex: 1;
}

.revenue-tickers {
  display: flex;
  gap: 16px;
}

.revenue-tickers > :deep(.card) {
  flex: 1;
  min-width: 150px;
  background: #023a6233;
}
</style>
