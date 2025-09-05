<template>
  <BaseCard :title="`Test ${symbol}`" :variant="variant">
    <div v-if="loading">Lade...</div>
    <div v-else>{{ revenueFormatted }}</div>
    <template #footer>
      <small>Quelle: SheetDB</small>
    </template>
  </BaseCard>
</template>

<script>
import BaseCard from "./Basecard.vue";
import { stockService } from "@/services/stockService";

export default {
  name: "RevenueCard",
  components: { BaseCard },
  props: { symbol: { type: String, required: true }, variant: { type: String, default: "default" } },
  data() {
    return { loading: true, revenue: [] };
  },
  async created() {
    this.revenue = await stockService.getRevenue(this.symbol);
    this.loading = false;
  },
  computed: {
    revenueFormatted() {
      return this.revenue.filter(v => v != null).join(" • ");
    },
  },
};
</script>
