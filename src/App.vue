<template>
  <main
    class="columns is-gapless is-multiline"
    :class="{ 'dark-theme': darkThemeActive }"
  >
    <div class="column is-one-quarter">
      <SideBar @toThemeChanged="changeTheme" />
    </div>
    <div class="column is-three-quarter content">
      <TaskForm @savingTask="saveTask" />
      <div v-if="tasks.length > 0" class="padding-20">
        <TaskView v-for="(task, index) in tasks" :key="index" :task="task" />
      </div>
      <div v-else class="padding-20">
        <CardBox> You're not very productive today :( </CardBox>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBar from "./components/SideBar.vue";
import TaskForm from "./components/Form.vue";
import TaskView from "./components/TaskView.vue";
import CardBox from "./components/CardBox.vue";
import ITask from "./interfaces/ITask";

export default defineComponent({
  name: "App",
  components: {
    SideBar,
    TaskForm,
    TaskView,
    CardBox,
  },
  data() {
    return {
      tasks: [] as ITask[],
      darkThemeActive: false,
    };
  },
  methods: {
    saveTask(task: ITask) {
      this.tasks.push(task);
    },
    changeTheme(darkThemeActive: boolean) {
      this.darkThemeActive = darkThemeActive;
    },
  },
});
</script>

<style>
.padding-20 {
  padding: 20px;
}

main {
  --bg-primary: #fff;
  --txt-primary: #000;
}
main.dark-theme {
  --bg-primary: #2b2d42;
  --txt-primary: #ddd;
  --color-secondary: #605f5f;
}
.content {
  background-color: var(--bg-primary);
}
</style>
