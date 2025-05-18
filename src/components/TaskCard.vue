<!-- src/components/TaskCard.vue -->
<template>
  <div
    class="p-4 bg-white rounded-lg shadow flex justify-between items-center"
  >
    <div>
      <h2 class="text-lg font-semibold">{{ task.title }}</h2>
      <p v-if="task.completed" class="text-green-500">✅ 已完成</p>
      <p v-else class="text-gray-500">⏳ 尚未完成</p>
    </div>

    <button
      v-if="!task.completed"
      class="bg-green-500 hover:bg-green-600 text-white px-3 py-1 rounded"
      @click="$emit('complete', task.id)"
    >
      完成
    </button>
  </div>
</template>

<script setup>
defineProps({
  task: {
    type: Object,
    required: true,
  },
})

defineEmits(['complete'])
</script>
