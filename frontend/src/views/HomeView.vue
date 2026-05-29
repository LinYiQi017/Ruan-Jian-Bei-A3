<script setup lang="ts">
import { ref } from 'vue'
import { useCounterStore } from '@/stores/counter'

const counter = useCounterStore()
const title = ref('Home Page')
</script>

<template>
  <div class="p-6 max-w-md mx-auto space-y-4">
    <h1 class="text-2xl font-bold">{{ title }}</h1>
    <p class="text-gray-600">This is a clean, minimal Vue 3 + Vite + Tailwind CSS + TypeScript project.</p>
    
    <div class="p-4 bg-gray-100 rounded-lg space-y-2">
      <h2 class="font-semibold">Pinia State (Counter): {{ counter.count }}</h2>
      <div class="flex gap-2">
        <el-button type="primary" size="small" @click="counter.increment">Increment</el-button>
        <el-button type="danger" size="small" @click="counter.decrement">Decrement</el-button>
      </div>
    </div>

    <div>
      <router-link to="/about" class="text-blue-500 hover:underline">Go to About Page</router-link>
    </div>
  </div>
</template>
