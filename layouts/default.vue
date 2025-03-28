<template>
  <header class="flex flex-row w-full items-center relative bg-green-400 border-b-2 border-gray-400 max-sm:justify-between max-sm:relative">
      <div class="basis-1/4 items-center justify-start px-8 min-w-40 max-sm:basis-auto">
          <img src="" class="w-16 h-16 bg-transparent" />
      </div>

      <div class="basis-1/4 max-sm:basis-auto"></div>

      <nav :class="{'basis-1/2 flex flex-row items-center justify-end px-8 gap-4': !burger, 'basis-auto max-sm:absolute max-sm:top-16 max-sm:w-full max-sm:justify-center max-sm:flex-col max-sm:gap-0 max-sm:bg-white max-sm:px-0': burger}">
          <NuxtLink to="/" class="my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 border-black max-sm:text-center">Home</NuxtLink>
          
          <div class="my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0" @click="switch_submenu">
              Labs
          </div>

          <div :class="{'max-sm:bg-red-100': submenu}" v-show="submenu" class="flex max-sm:flex-col max-sm:w-full max-sm:border-b-2 max-sm:relative max-sm:w-full">
              <NuxtLink to="/Lab3" class="my-auto p-2 border-b-2 border-black hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-t-2 max-sm:text-center">Lab3</NuxtLink>
              <NuxtLink to="/Lab4" class="my-auto p-2 border-b-2 border-black hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:text-center">Lab4</NuxtLink>
              <NuxtLink to="/Lab5" class="my-auto p-2 border-b-2 border-black hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:text-center">Lab5</NuxtLink>
              <NuxtLink to="/Lab6" class="my-auto p-2 border-b-2 border-black hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:text-center">Lab6</NuxtLink>
          </div>

          <NuxtLink to="/login" :class="{'my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 border-black max-sm:text-center': submenu, 'my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-t-2 max-sm:text-center': !submenu}">
              LogIn
          </NuxtLink>

          <NuxtLink to="/logout" class="my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:text-center">LogOut</NuxtLink>
      </nav>

      
      <div v-if="!burger" @click="switch_burger" class="max-sm:flex max-sm:flex-col max-sm:justify-between max-sm:mr-8 max-sm:h-6">
          <span class="h-[3px] w-full bg-blue-950"></span>
          <span class="h-[3px] w-full bg-blue-950"></span>
          <span class="h-[3px] w-full bg-blue-950"></span>
      </div>
      <div v-else class="max-sm:flex max-sm:flex-col max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6" @click="switch_burger">
          <span class="h-[3px] w-full bg-blue-950 rotate-45 relative top-[9px]"></span>
          <span class="h-[3px] w-full bg-blue-950 opacity-0"></span>
          <span class="h-[3px] w-full bg-blue-950 relative bottom-3 rotate-[-45deg]"></span>
      </div>
  </header>

  <main class="p-5 flex bg-green-100 h-screen">
      <slot />
  </main>

  <footer class="flex flex-row w-full bg-green-400 border-t-2 border-gray-400 items-center justify-center px-4 py-2 gap-4">
      <a href="https://www.youtube.com/">
          <img src="assets/images/youtube.png" class="w-16 h-16" />
      </a>
      <a href="https://github.com/">
          <img src="assets/images/github.png" class="w-16 h-16" />
      </a>
      <a href="https://www.facebook.com/">
          <img src="assets/images/facebook.png" class="w-16 h-16 bg-transparent" />
      </a>
  </footer>
</template>

<script setup>
import { ref } from 'vue'

const burger = ref(false)
const submenu = ref(false)

function switch_burger() {
  burger.value = !burger.value
}

function switch_submenu() {
  submenu.value = !submenu.value
}
</script>
