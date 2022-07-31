<template>
  <div class="box form">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Create a new task form">
        <input
          type="text"
          class="input"
          placeholder="Task to init"
          v-model="taskDescription"
        />
      </div>
      <div class="column">
        <TaskTimer @finalized="stopTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TaskTimer from "./TaskTimer.vue";

export default defineComponent({
  name: "TaskForm",
  components: { TaskTimer },
  data() {
    return {
      taskDescription: "",
    };
  },
  methods: {
    stopTask(timer: number): void {
      this.$emit("savingTask", {
        duration: timer,
        description: this.taskDescription,
      });
      this.taskDescription = "";
    },
  },
  emits: ["savingTask"],
});
</script>

<style>
.form {
  color: var(--txt-primary);
  background-color: var(--bg-primary);
  box-shadow: none;
  border-bottom: 1px solid var(--color-secondary);
  border-radius: 0;
}
</style>
