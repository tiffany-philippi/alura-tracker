<template>
  <CardBox>
    <div class="columns">
      <div class="column is-7">
        {{ task.description || "Task with no description" }}
      </div>
      <div class="column">
        <Chronometer :timer="task.duration" />
      </div>
    </div>
  </CardBox>
</template>

<script lang="ts">
import ITask from "@/interfaces/ITask";
import { defineComponent, PropType } from "vue";
import Chronometer from "./Chronometer.vue";
import CardBox from "./CardBox.vue";

export default defineComponent({
  name: "TaskView",
  components: { Chronometer, CardBox },
  props: {
    task: {
      type: Object as PropType<ITask>,
      required: true,
    },
  },
});
</script>

<style scoped></style>
