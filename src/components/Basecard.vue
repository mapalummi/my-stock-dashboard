<template>
  <div class="card" :class="variantClass">
    <div v-if="title || $slots.header" class="card-header">
      <slot name="header">
        <h2>{{ title }}</h2>
      </slot>
    </div>
    <div class="card-content">
      <slot>
        <p>Hier kommt dein Inhalt hin.</p>
      </slot>
    </div>
    <div v-if="$slots.footer" class="card-footer">
      <slot name="footer" />
    </div>
  </div>
</template>

<script>
export default {
  name: "BaseCard",
  props: {
    title: {
      type: String,
      default: "",
    },
    variant: { type: String, default: "default" },
  },
  computed: {
    variantClass() {
      return {
        "card--full": this.variant === "full",
        "card--square": this.variant === "square",
      };
  },
},
};
</script>

<style scoped>
.card {
  background-color: #011f35;
  border-radius: 16px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  padding: 24px 32px;
  margin: 1rem 0;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  display: flex;
  flex-direction: column;
  max-width: 100%;
}

.card-header h2 {
  margin: 0 0 1rem;
  font-size: 1.25rem;
  font-weight: bold;
  color: white;
}

.card-content {
  flex: 1;
  color: white;
  font-size: 1rem;
  line-height: 1.5;
}

.card-footer {
  margin-top: 1rem;
  font-size: 0.8rem;
  text-align: right;
  color: white;
}

/* Varianten */
.card--full {
  width: 100%;
}

.card--square {
  aspect-ratio: 1 / 1;
  width: 100%;
  max-height: 250px;
  overflow: auto;
}
</style>
