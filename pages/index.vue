<template>
  <div class="min-h-screen w-full bg-black text-white flex flex-col items-center justify-center p-6">
    
    
    <h1 class="text-3xl sm:text-4xl md:text-5xl font-extrabold mb-4 animate-pulse text-center">
      𓆩ZXC COMPANY𓆪
    </h1>
    <p class="text-lg text-gray-300 mb-8 text-center max-w-xl tracking-wide">
      𝐌𝐄𝐄𝐓 𝐎𝐔𝐑 𝐓𝐄𝐀𝐌
    </p>

    
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-8">
      <div
        v-for="(pic, index) in pics"
        :key="index"
        class="flex flex-col items-center bg-gradient-to-b from-gray-800 to-gray-900 p-4 rounded-2xl shadow-lg transform hover:scale-105 hover:rotate-1 transition-all duration-500 ease-in-out border border-gray-700 hover:border-purple-500"
      >
        <img
          :src="pic.image"
          :alt="pic.name"
          class="w-48 h-48 rounded-xl mb-4 shadow-md hover:shadow-purple-500/50 transition-all duration-500"
        />
        <p class="text-xl font-semibold text-white">{{ pic.name }}</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue'

interface stkimg {
  name: string
  image: string
}

const pics = reactive<stkimg[]>([
  { name: 'Ghoul', image: '/zxc.png' },
  { name: 'Mirai', image: '/mirai.png' },
  { name: 'Ken', image: '/ken.png' }
])
</script>




