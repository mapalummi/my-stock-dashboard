<template>
    <BaseCard title="Net Income" :variant="variant">
      <p>Here goes the content</p>
    </BaseCard>
  </template>
  
  <script>
  import BaseCard from "./Basecard.vue";
  export default {
    name: "NetIncomeCard",
    components: { BaseCard },
    props: { variant: { type: String, default: "default" } },
  };
  </script>
  