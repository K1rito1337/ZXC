<template>
  <div class="bg-black min-h-screen text-white flex items-center justify-center">
    <div class="flex flex-col items-center text-center">
      
      
      <img 
        src="/logout.gif" 
        alt="Animation 1" 
        class="w-96 h-64 mb-6 rounded-xl shadow-lg object-cover"
      />

      
      <h1 class="text-2xl font-extrabold mb-4 animate-pulse">
      Logout 𓆩ZXC COMPANY𓆪
    </h1>

      
      <button
  @click="logout"
  class="mt-6 w-64 px-6 py-3 bg-red-600 text-white font-semibold rounded-lg hover:bg-red-800 shadow-lg transition duration-300"
>
  ⋆.˚✮Logout🎧✮˚.⋆
</button>
    </div>
  </div>
</template>

<script setup>
const logout = () => {
  localStorage.removeItem("loggedout");
  alert("You are logged out!");
  window.location.href = "/logout"; 
};
</script>
