<template>
  <div class="mx-auto bg-black min-h-screen text-white flex flex-col items-center py-10 px-6">
    <!-- Заголовок -->
    <h1 class="text-5xl font-extrabold mb-2 text-center tracking-wide">
      𓆩ZXC COMPANY𓆪
    </h1>
    <p class="text-lg text-gray-400 font-semibold mb-10 tracking-widest text-center">
      Member of the Cleaners' Team Akuta
    </p>

    <!-- Радиокнопки -->
    <div class="mb-10 mx-5 p-2 rounded-full bg-gray-900 shadow-lg">
      <div class="flex flex-wrap justify-center gap-4">
        <label
          v-for="team in teams"
          :key="team"
          class="flex flex-row items-center space-x-2 cursor-pointer select-none rounded-lg transition-all duration-300"
          role="button"
          :class="{
            'bg-purple-700 shadow-md pl-4 pr-6 py-2': selectedTeam === team,
            'hover:bg-gray-700 hover:shadow-md pl-4 pr-6 py-2': selectedTeam !== team
          }"
        >
          <input type="radio" v-model="selectedTeam" :value="team" class="hidden" />
          <span class="text-white font-semibold">{{ team }}</span>
        </label>
      </div>
    </div>

    <!-- Карточки участников -->
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-10">
      <div
        v-for="member in filteredMembers"
        :key="member.id"
        class="relative flex flex-col items-center bg-gradient-to-b from-gray-800 to-gray-900 p-4 rounded-2xl shadow-lg border border-gray-700 hover:border-purple-500 transform hover:scale-105 transition-all duration-500 ease-in-out group"
      >
        <!-- Изображение -->
        <div class="relative overflow-hidden rounded-xl mb-4 border border-gray-700 w-56 h-56">
          <img
            :src="member.image"
            :alt="member.name"
            class="w-full h-full object-cover rounded-xl transition-transform duration-500 group-hover:scale-110"
          />

          <!-- Описание при наведении -->
          <div
            class="absolute inset-0 bg-black/80 opacity-0 group-hover:opacity-100 flex items-center justify-center p-4 transition-all duration-500"
          >
            <p class="text-gray-300 text-center text-sm leading-relaxed">
              {{ member.description }}
            </p>
          </div>
        </div>

        <!-- Имя и роль -->
        <p class="text-xl font-semibold text-gray-100">{{ member.name }}</p>
        <p class="text-sm text-gray-400">{{ member.team }}</p>
      </div>
    </div>

    <!-- Если нет участников -->
    <div v-if="filteredMembers.length === 0" class="text-center py-8 text-gray-400">
      <p class="text-lg">No members found</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref, computed } from 'vue'

interface Member {
  id: number
  name: string
  image: string
  team: string
  description: string
}

const members = reactive<Member[]>([
  {
    id: 1,
    name: 'Rudo',
    image: '/chara_list_1.png',
    team: 'Main',
    description: 'Silent leader. Cold, calm, and tactical — always stays in control.'
  },
  {
    id: 2,
    name: 'Enjin',
    image: '/chara_list_2.png',
    team: 'Art',
    description: 'Creative mind who turns chaos into style and vision.'
  },
  {
    id: 3,
    name: 'Zanka',
    image: '/chara_list_3.png',
    team: 'Tech',
    description: 'Code machine. Writes scripts faster than lightning.'
  },
  {
    id: 4,
    name: 'Riyo',
    image: '/chara_list_4.png',
    team: 'Main',
    description: 'Analyst and strategist — always sees two steps ahead.'
  },
  {
    id: 5,
    name: 'Corvus',
    image: '/chara_list_19.png',
    team: 'Media',
    description: 'Calm energy, strong presence.'
  }
])

const teams = ['All', 'Main', 'Tech', 'Art', 'Media']
const selectedTeam = ref('All')

const filteredMembers = computed(() => {
  if (selectedTeam.value === 'All') return members
  return members.filter(member => member.team === selectedTeam.value)
})
</script>

<style scoped>
h1 {
  text-shadow: 0 0 10px rgba(147, 51, 234, 0.5);
}
</style>

