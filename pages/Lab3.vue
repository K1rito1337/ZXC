<template>
  <div class="mx-auto bg-black min-h-screen text-white">
    <!-- Заголовок -->
    <div class="text-center pt-10">
      <h1 class="text-4xl sm:text-5xl font-extrabold mb-3 animate-pulse">𓆩ZXC COMPANY𓆪</h1>
      <p class="text-lg text-gray-400 mb-6">𝐓𝐄𝐀𝐌 𝐌𝐄𝐌𝐁𝐄𝐑𝐒</p>
    </div>

    <!-- Радиокнопки фильтра -->
    <div class="mb-8 mx-5 p-0.5 rounded-full bg-gray-900 shadow-lg">
      <div class="flex flex-wrap justify-center gap-4">
        <label
          v-for="filter in filters"
          :key="filter"
          class="flex flex-row items-center space-x-2 cursor-pointer select-none rounded-lg transition-all duration-300"
          role="button"
          :class="{
            'bg-purple-700 shadow-md pl-3 pr-5 my-1 py-3': selectedFilter === filter,
            'hover:bg-gray-700 hover:shadow-md pl-3 pr-5 my-1 py-3': selectedFilter !== filter
          }"
        >
          <input
            type="radio"
            v-model="selectedFilter"
            :value="filter"
            class="hidden"
          />
          <span class="text-white font-semibold">{{ filter }}</span>
        </label>
      </div>
    </div>

    <!-- Карточки участников -->
    <div class="px-8 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 pb-10">
      <div
        v-for="member in filteredMembers"
        :key="member.id"
        class="bg-gradient-to-b from-gray-800 to-gray-900 rounded-2xl shadow-lg hover:scale-[1.03] overflow-hidden hover:shadow-purple-500/40 transition-all duration-500 ease-in-out"
      >
        <div class="relative group">
          <img
            :src="member.image"
            :alt="member.name"
            class="w-full h-64 object-cover rounded-t-2xl transition-transform duration-500 group-hover:scale-105"
          />
          <div
            class="absolute inset-0 bg-black/70 opacity-0 group-hover:opacity-100 flex items-center justify-center p-4 transition-all duration-500"
          >
            <p class="text-gray-300 text-center text-sm leading-relaxed">{{ member.description }}</p>
          </div>
        </div>
        <div class="p-4 text-center">
          <h3 class="text-xl font-bold mb-1">{{ member.name }}</h3>
          <p class="text-sm text-gray-400">{{ member.role }}</p>
        </div>
      </div>
    </div>

    <!-- Нет участников -->
    <div v-if="filteredMembers.length === 0" class="text-center py-8 text-gray-400">
      <p class="text-lg">No team members found</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref, computed } from 'vue'

interface Member {
  id: number
  name: string
  image: string
  role: string
  description: string
  team: string
}

const members = reactive<Member[]>([
  {
    id: 1,
    name: 'Ghoul',
    image: '/zxc.gif',
    role: 'Leader',
    description: 'Cold and silent, but strategic — leads the team to victory.',
    team: 'Main'
  },
  {
    id: 2,
    name: 'Mirai',
    image: '/mirai.gif',
    role: 'Designer',
    description: 'Brings chaos and creativity to every project.',
    team: 'Art'
  },
  {
    id: 3,
    name: 'Ken',
    image: '/ken.gif',
    role: 'Developer',
    description: 'Writes code faster than you can blink.',
    team: 'Tech'
  },
  {
    id: 4,
    name: 'Rei',
    image: '/rei.gif',
    role: 'Analyst',
    description: 'Sees every move before it happens.',
    team: 'Main'
  },
  {
    id: 5,
    name: 'Luna',
    image: '/luna.gif',
    role: 'PR Manager',
    description: 'Voice of ZXC — calm but deadly.',
    team: 'Media'
  }
])

const filters = ['All', 'Main', 'Tech', 'Art', 'Media']
const selectedFilter = ref('All')

const filteredMembers = computed(() => {
  if (selectedFilter.value === 'All') return members
  return members.filter(member => member.team === selectedFilter.value)
})
</script>

<style scoped>
input[type="radio"] {
  @apply w-4 h-4;
}

img {
  @apply rounded-xl;
}
</style>

