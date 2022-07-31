<template>
  <section>
    <strong class="display">
      {{ formatTime }}
    </strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "TaskChronometer",
  props: {
    timer: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    formatTime(): string {
      return new Date(this.timer * 1000).toISOString().substring(19, 11);
    },
  },
});
</script>

<style>
.display {
  color: var(--txt-primary);
}
</style>
