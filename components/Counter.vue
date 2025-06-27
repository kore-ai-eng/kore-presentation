<script setup lang="ts">
import { ref, watch } from 'vue'

interface Props {
  count?: number
}

const props = defineProps<Props>()

// Initialize the counter value with props.count or default to 0
const counter = ref<number>(props.count ?? 0)

// Watch for changes to the count prop and update the counter accordingly
watch(
  () => props.count,
  (newVal) => {
    if (typeof newVal === 'number') {
      counter.value = newVal
    }
  }
)
</script>

<template>
  <div class="flex items-center justify-center border border-main rounded-md min-w-min">
    <button
      class="border-r border-main p-2 font-mono outline-none hover:bg-gray-400 hover:opacity-20"
      @click="counter--"
    >
      -
    </button>
    <span class="mx-auto p-2">{{ counter }}</span>
    <button
      class="border-l border-main p-2 font-mono outline-none hover:bg-gray-400 hover:opacity-20"
      @click="counter++"
    >
      +
    </button>
  </div>
</template>

<style scoped>
/* You can add component-specific styles here if necessary */
</style>