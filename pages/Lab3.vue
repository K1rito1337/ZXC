<template>
  <div class="min-h-screen w-full bg-black text-white flex flex-col items-center justify-center p-6">
    <!-- Заголовок -->
    <h1 class="text-3xl sm:text-4xl md:text-5xl font-extrabold mb-4 animate-pulse text-center">
      𓆩ZXC COMPANY𓆪
    </h1>
    <p class="text-lg text-gray-300 mb-8 text-center max-w-xl">
      𝐓𝐄𝐀𝐌 𝐌𝐄𝐌𝐁𝐄𝐑𝐒
    </p>

    <!-- Карточки -->
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-8">
      <div class="flex flex-col items-center bg-gradient-to-b from-gray-800 to-gray-900 p-4 rounded-2xl shadow-lg border border-gray-700 hover:border-purple-500 transform hover:scale-105 transition-all duration-500 ease-in-out">
        <img :src="pic1.image" class="w-48 h-48 rounded-xl mb-4 shadow-md hover:shadow-purple-500/50 transition-all duration-500" />
        <p class="text-xl font-semibold">{{ pic1.name }}</p>
      </div>

      <div class="flex flex-col items-center bg-gradient-to-b from-gray-800 to-gray-900 p-4 rounded-2xl shadow-lg border border-gray-700 hover:border-purple-500 transform hover:scale-105 transition-all duration-500 ease-in-out">
        <img :src="pic2.image" class="w-48 h-48 rounded-xl mb-4 shadow-md hover:shadow-purple-500/50 transition-all duration-500" />
        <p class="text-xl font-semibold">{{ pic2.name }}</p>
      </div>

      <div class="flex flex-col items-center bg-gradient-to-b from-gray-800 to-gray-900 p-4 rounded-2xl shadow-lg border border-gray-700 hover:border-purple-500 transform hover:scale-105 transition-all duration-500 ease-in-out">
        <img :src="pic3.image" class="w-48 h-48 rounded-xl mb-4 shadow-md hover:shadow-purple-500/50 transition-all duration-500" />
        <p class="text-xl font-semibold">{{ pic3.name }}</p>
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

const pic1 = reactive<stkimg>({
  name: 'Ghoul',
  image: '/zxc.gif'
})

const pic2 = reactive<stkimg>({
  name: 'Mirai',
  image: '/mirai.gif'
})

const pic3 = reactive<stkimg>({
  name: 'Ken',
  image: '/ken.gif'
})
</script>
