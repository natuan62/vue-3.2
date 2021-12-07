<script setup lang="ts">
import { reactive } from 'vue';
import Counter from './components/Counter.vue';

interface AppInfo {
  name: string;
}

const appInfo: AppInfo = reactive({
  name: 'Counter',
});
</script>

<template>
  <div class="wrapper">
    <h1>{{ appInfo.name }}</h1>
    <Counter class="blue"></Counter>
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
