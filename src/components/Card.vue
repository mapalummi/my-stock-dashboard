<template>
  <div class="card">
    <!-- Optionaler Header -->
    <div v-if="title" class="card-header">
      <h2>{{ title }}</h2>
    </div>

    <!-- Hauptinhalt -->
    <div class="card-content">
      <slot>
        <!-- Fallback-Content, falls kein Slot übergeben wird -->
        <p>Hier kommt dein Inhalt hin.</p>
      </slot>
    </div>

    <!-- Optionaler Footer -->
    <div v-if="$slots.footer" class="card-footer">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "BaseCard",
  props: {
    title: {
      type: String,
      default: ""
    }
  }
};
</script>

<style scoped>
.card {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  padding: 1.5rem;
  margin: 1rem 0;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  display: flex;
  flex-direction: column;
  max-width: 400px;
}

/* Hover-Effekt */
.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.15);
}

.card-header h2 {
  margin: 0 0 1rem;
  font-size: 1.25rem;
  font-weight: bold;
  color: #2c3e50;
}

.card-content {
  flex: 1;
  color: #555;
  font-size: 1rem;
  line-height: 1.5;
}

.card-footer {
  margin-top: 1rem;
  text-align: right;
}
</style>
