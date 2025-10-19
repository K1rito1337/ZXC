<template>
  <div class="min-h-screen flex flex-col bg-black text-white">
    
    
    <header class="flex w-full items-center justify-between bg-black shadow-sm py-2 sticky top-0 z-50 text-gray-500">
      <div class="basis-1/4 flex items-center justify-start px-8 min-w-40 max-sm:basis-auto">
        <img 
          src="/IMG_1397.gif" 
          alt="Logo"
          class="w-20 h-20 rounded-full p-1 shadow-lg 
                 bg-black
                 hover:scale-110 hover:rotate-3 transition-transform duration-500 ease-in-out
                 hover:shadow-[0_0_20px_4px_rgba(185,28,28,0.7)]"
        />
      </div>

      <div class="basis-1/4 max-sm:basis-auto"></div>
      <nav :class="{
        'basis-1/2 flex flex-row items-center justify-end px-2 gap-2': !burger || burger,
        'max-sm:basis-auto max-sm:absolute max-sm:top-full max-sm:w-full max-sm:justify-center max-sm:flex-col max-sm:gap-0 max-sm:bg-black max-sm:px-0': burger,
        'max-sm:hidden': !burger,}">
        
        
        <NuxtLink 
          to="/" 
          @click="burger = false" 
          class="my-auto px-4 py-2 rounded-lg shadow-lg
                 bg-red-700
                 text-white font-medium
                 transition-transform duration-500 ease-in-out
                 hover:scale-110 hover:rotate-1
                 hover:shadow-[0_0_15px_3px_rgba(185,28,28,0.7)] 
                 max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0">
          Home
        </NuxtLink>

        
        <div @click="switch_submenu" 
          class="my-auto px-4 py-2 rounded-lg shadow-lg
                 bg-red-700
                 text-white font-medium cursor-pointer
                 transition-transform duration-500 ease-in-out
                 hover:scale-110 hover:rotate-1
                 hover:shadow-[0_0_15px_3px_rgba(185,28,28,0.7)] 
                 max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0">
          Labs
        </div>

       
        <div
          class="flex flex-col absolute right-0 top-full bg-black text-white w-56 text-left shadow-lg rounded mt-1 z-40 max-sm:static max-sm:w-56 max-sm:mx-auto max-sm:mt-2"
          v-show="submenu"
        >
          <NuxtLink to="/lab3" @click="burger = false" class="px-4 py-2 hover:bg-red-700 transition">Lab3</NuxtLink>
          <NuxtLink to="/lab4" @click="burger = false" class="px-4 py-2 hover:bg-red-700 transition">Lab4</NuxtLink>
          <NuxtLink to="/lab5" @click="burger = false" class="px-4 py-2 hover:bg-red-700 transition">Lab5</NuxtLink>
          <NuxtLink to="/lab6" @click="burger = false" class="px-4 py-2 hover:bg-red-700 transition">Lab6</NuxtLink>
        </div>

        
        <NuxtLink 
          to="/login" 
          @click="burger = false" 
          class="my-auto px-4 py-2 rounded-lg shadow-lg
                 bg-red-700
                 text-white font-medium
                 transition-transform duration-500 ease-in-out
                 hover:scale-110 hover:rotate-1
                 hover:shadow-[0_0_15px_3px_rgba(185,28,28,0.7)] 
                 max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0">
          LogIn
        </NuxtLink>

        
        <NuxtLink 
          to="/logout" 
          @click="burger = false" 
          class="my-auto px-4 py-2 rounded-lg shadow-lg
                 bg-red-700
                 text-white font-medium
                 transition-transform duration-500 ease-in-out
                 hover:scale-110 hover:rotate-1
                 hover:shadow-[0_0_15px_3px_rgba(185,28,28,0.7)] 
                 max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0">
          LogOut
        </NuxtLink>
      </nav>

      
      <div
        v-if="!burger"
        @click="switch_burger"
        class="max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6"
      >
        <span class="h-[3px] w-full bg-white"></span>
        <span class="h-[3px] w-full bg-white"></span>
        <span class="h-[3px] w-full bg-white"></span>
      </div>
    </header>

   
    <main class="flex-grow flex items-center justify-center p-6 bg-black">
      <slot />
    </main>

    
    <footer class="flex flex-col w-full bg-black items-center justify-center px-4 py-6 gap-4">
      <div class="flex flex-row gap-6">
        <a href="https://www.youtube.com"><img src="/youtube.png" class="w-12 h-12"></a>
        <a href="https://web.telegram.org"><img src="/telegram.png" class="w-12 h-12"></a>
        <a href="https://www.instagram.com"><img src="/instagram.png" class="w-12 h-12"></a>
      </div>
      <div class="text-xs text-center text-gray-400">© 2025 Your Site</div>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { useHead } from "#app";
import { ref } from "vue";

useHead({
  script: [
    {
      async: true,
      src: 'https://www.googletagmanager.com/gtag/js?id=G-D7XNJ44EM7',
    },
    {
      innerHTML: `
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());
        gtag('config', 'G-D7XNJ44EM7');            
      `,
      type: 'text/javascript',
    },
  ],
  _dangerouslyDisableSanitizersByTagID: {
    gtag: ['innerHTML'],
  },
})

const burger = ref<boolean>(false)
const submenu = ref<boolean>(false)

const switch_burger = () => (burger.value = !burger.value)
const switch_submenu = () => (submenu.value = !submenu.value)
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background-color: black; 
}
</style>
