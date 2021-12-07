<template>
  <p v-if="error">{{ error }}</p>
  <img v-else :src="imgUrl" />
</template>

<script setup lang="ts">
import { ref } from 'vue';

const imgUrl = ref<string>();
const error = ref();

try {
  imgUrl.value = await fetch('https://picsum.photos/200').then((res) => res.url);
} catch (e) {
  error.value = e;
}
</script>
