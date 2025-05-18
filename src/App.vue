<template>
  <div class="min-h-screen bg-gray-100 p-4">
    <div class="max-w-3xl mx-auto">
      <h1 class="text-3xl font-bold mb-4">🎯 今日任務</h1>

      <div class="space-y-4">
        <TaskCard
          v-for="task in tasks"
          :key="task.id"
          :task="task"
          @complete="completeTask"
        />
      </div>

      <div class="mt-6">
        <button
          class="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded-xl shadow-md"
          @click="addSampleTask"
        >
          ➕ 新增任務
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import TaskCard from './components/TaskCard.vue'

const tasks = ref([
  { id: 1, title: '完成 Vue 任務 UI', completed: false },
  { id: 2, title: '整理 ERD 資料表結構', completed: false },
])

function completeTask(id) {
  const task = tasks.value.find((t) => t.id === id)
  if (task) task.completed = true
}

function addSampleTask() {
  const id = Date.now()
  tasks.value.push({ id, title: '新的任務項目', completed: false })
}
</script>
