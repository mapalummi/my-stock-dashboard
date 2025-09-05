<template>
    <BaseCard title="Revenue Growth" :variant="variant">
      <p>Here goes the content</p>
    </BaseCard>
  </template>
  
  <script>
  import BaseCard from "./Basecard.vue";
  export default {
    name: "RevenueGrowthCard",
    components: { BaseCard },
    props: { variant: { type: String, default: "default" } },
  };
  </script>
  