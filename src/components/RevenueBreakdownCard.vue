<template>
  <BaseCard title="Revenue Breakdown" :variant="variant">
    <ul>
      <li v-for="t in tickers" :key="t">{{ t }}</li>
    </ul>
  </BaseCard>
</template>

<script>
import BaseCard from "./Basecard.vue";
export default {
  name: "RevenueBreakdownCard",
  components: { BaseCard },
  props: { tickers: { type: Array, default: () => ["$AAPL", "$MSFT"] }, variant: { type: String, default: "default" } },
};
</script>
