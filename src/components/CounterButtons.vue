<script setup lang="ts">
import { ref } from 'vue';

const emit = defineEmits<{
  (event: 'add-count', num: number): void;
  (event: 'reset-count'): void;
}>();

const btnColor = ref<string>();

const addCount = () => {
  emit('add-count', 1);
};

const resetCount = () => {
  emit('reset-count');
};

const changeColor = (): void => {
  btnColor.value = '#' + (Math.random().toString(16) + '00000').slice(2, 8);
};
</script>

<template>
  <p>
    <button @click="addCount()">Add</button>
    <button @click="resetCount()">Reset</button>
  </p>
  <p>
    <button @click="changeColor()">Change Color</button>
  </p>
</template>

<style>
button {
  margin: 5px;
  color: v-bind(btnColor);
  border: none;
  padding: 15px 32px;
  font-size: 16px;
}
</style>
