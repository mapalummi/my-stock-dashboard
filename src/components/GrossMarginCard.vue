<template>
    <BaseCard title="Gross Margin" :variant="variant">
      <p>Here goes the content</p>
    </BaseCard>
  </template>
  
  <script>
  import BaseCard from "./Basecard.vue";
  export default {
    name: "GrossMarginCard",
    components: { BaseCard },
    props: { variant: { type: String, default: "default" } },
  };
  </script>
  