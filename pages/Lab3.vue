<template>
  <main class="flex flex-row gap-4 justify-center items-center h-screen bg-gradient-to-b from-gray-200 to-blue-300 hover:to-red-300 flex-wrap">
    <div class="flex flex-col gap-2 border-blue-500 border-1 bg-blue-300 w-72 h-auto items-center hover:border-red-500 border-2 hover:bg-red-300 rounded-xl">
      <img :src="pic1.image" class="w-60 h-60 pt-2">
      <p class="text-black text-xl">{{pic1.name}}</p>
    </div>

    <div class="flex flex-col gap-2 border-blue-500 border-1 bg-blue-300 w-72 h-auto items-center hover:border-red-500 border-2 hover:bg-red-300 rounded-xl">
      <img :src="pic2.image" class="w-60 h-60 pt-2">
      <p class="text-black text-xl">{{pic2.name}}</p>
    </div>

    <div class="flex flex-col gap-2 border-blue-500 border-1 bg-blue-300 w-72 h-auto items-center hover:border-red-500 border-2 hover:bg-red-300 rounded-xl">
      <img :src="pic3.image" class="w-60 h-60 pt-2">
      <p class="text-black text-xl">{{pic3.name}}</p>
    </div>
  </main>
</template>

<script setup lang="ts">
import { reactive } from 'vue'

interface stkimg {
  name: string,
  image: string
}

const pic1 = reactive<stkimg>({
  name: 'Ghoul',
  image: 'zxc.png'
})

const pic2 = reactive<stkimg>({
  name: 'Mirai',
  image: 'mirai.png'
})

const pic3 = reactive<stkimg>({
  name: 'Ken',
  image: 'ken.png'
})
</script>
