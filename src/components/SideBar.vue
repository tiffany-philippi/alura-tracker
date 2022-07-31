<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="logo" />
    </h1>
    <button class="button" @click="changeTheme">{{ buttonText }}</button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SideBar",
  data() {
    return {
      darkThemeActive: false,
    };
  },
  emits: ["toThemeChanged"],
  computed: {
    buttonText() {
      return this.darkThemeActive
        ? "Disable dark theme"
        : "Activate dark theme";
    },
  },
  methods: {
    changeTheme() {
      this.darkThemeActive = !this.darkThemeActive;
      this.$emit("toThemeChanged", this.darkThemeActive);
    },
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
