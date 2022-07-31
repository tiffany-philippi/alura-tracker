<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <TaskChronometer :timer="timeInSeconds" />
        <button class="button" @click="start" :disabled="isActive">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="stop" :disabled="!isActive">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TaskChronometer from './Chronometer.vue';

export default defineComponent({
    name: 'TaskTimer',
    emits: ['finalized'],
    data() {
        return {
            timeInSeconds: 0,
            timer: 0,
            isActive: false
        };
    },
    methods: {
        start() {
            this.isActive = true;
            this.timer = setInterval(() => {
                this.timeInSeconds += 1;
            }, 1000);
        },
        stop() {
            this.isActive = false;
            clearInterval(this.timer);
            this.$emit('finalized', this.timeInSeconds);
            this.timeInSeconds = 0
        }
    },
    components: { TaskChronometer }
});
</script>

<style scoped>
</style>