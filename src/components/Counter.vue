<script lang="ts">
import { defineAsyncComponent } from 'vue';
import TopLevelAwait from './TopLevelAwait.vue';

export default {
  inheritAttrs: false,
  components: {
    TopLevelAwait: defineAsyncComponent(() => import('./TopLevelAwait.vue')),
  },
};
</script>

<script setup lang="ts">
import { useAttrs, ref } from 'vue';
import CounterButtons from './CounterButtons.vue';

interface Props {
  limit?: number;
}

const props = withDefaults(defineProps<Props>(), {
  limit: 5,
});

const attrs = useAttrs();

const count = ref<number>(0);

const addCountEmit = (num: number): void => {
  if (count.value >= props.limit) {
    count.value = 0;
  } else {
    count.value += num;
  }
};

const resetCountEmit = (): void => {
  count.value = 0;
};

</script>

<template>
  <suspense>
    <template #default>
      <TopLevelAwait />
    </template>
    <template #fallback>
      <p>Loading...</p>
    </template>
  </suspense>
  <p v-bind="attrs">{{ count }}</p>
  <CounterButtons @add-count="addCountEmit" @reset-count="resetCountEmit" />
</template>

<style scoped>
.blue {
  color: blue;
  font-size: 20px;
  font-weight: 800;
}
</style>
