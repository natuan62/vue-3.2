<script setup lang="ts">
const emit = defineEmits<{
  (event: 'add-count', num: number): void;
  (event: 'reset-count'): void;
}>();

const addCount = () => {
  emit('add-count', 1);
};

const resetCount = () => {
  emit('reset-count');
};
</script>

<template>
  <p>
    <button @click="addCount()">Add</button>
    <button @click="resetCount()">Reset</button>
  </p>
</template>

<style>
button {
  margin: 5px;
}
</style>
