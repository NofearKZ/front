<template>
<div>
    <h1>this is lab 3 page</h1>
</div>

  <main class="flex flex-col gap-4 p-12 justify-center min-h-screen items-center bg-gradient-to-b from-gray-200 to-red-500 hover:to-green-400
  -300 flex-wrap">

    <div class="flex gap-4">
      <label><input class="mx-2" type="radio" value="Goku" v-model="selectedpic">Goku</label>
      <label><input class="mx-2" type="radio" value="Vegeta" v-model="selectedpic">Vegeta</label>
      <label><input class="mx-2" type="radio" value="Gogeta" v-model="selectedpic">Gogeta</label>
    </div>

    <div class="flex flex-row gap-4 flex-wrap">

      <div class="blockcap" v-if="selectedpic == 'Goku'">
        <img :src="pic1.image" class="w-60 h-68 pt-2">
        <p class="text-black text-xl">{{ pic1.name }}</p>
      </div>

      <div class="blockcap" v-if="selectedpic == 'Vegeta'">
        <img :src="pic2.image" class="w-60 h-68 pt-2">
        <p class="text-black text-xl">{{ pic2.name }}</p>
      </div>

      <div class="blockcap" v-if="selectedpic == 'Gogeta'">
        <img :src="pic3.image" class="w-60 h-68 pt-2">
        <p class="text-black text-xl">{{ pic3.name }}</p>
      </div>

    </div>

    <div class="flex flex-row gap-4 flex-wrap">
      <div class="blockfor" v-for="(pic, index) in genpic" :key="index">
        <img :src="pic.image" class="w-60 h-68 pt-2">
        <p class="text-black text-xl">{{ pic.name }}</p>
      </div>
    </div>

  </main>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'

interface stking {
  name: string,
  image: string
}

const pic1 = reactive<stking>({
  name: 'Goku',
  image:'/images/Goku.png'
})

const pic2 = reactive<stking>({
  name: 'Vegeta',
  image: '/images/vegeta.png'
})

const pic3 = reactive<stking>({
  name: 'Gogeta',
  image: '/images/Gogeta.png'
})

const genpic = reactive<stking[]>([
  { name: 'Goku', image:  '/images/Goku.png' },
  { name: 'Vegeta', image: '/images/vegeta.png' },
  { name: 'Gogeta', image: '/images/Gogeta.png' }
])

const selectedpic = ref<string>('')
</script>

<style scoped>
.blockcap {
  @apply flex flex-col gap-2 border border-blue-500 bg-green-300 w-72 h-auto items-center hover:border-blue-500 hover:border-4 hover:bg-blue-300 rounded-xl;
}
.blockfor {
  @apply flex flex-col gap-2 border border-blue-500 bg-green-300 w-72 h-auto items-center hover:border-red-500 hover:border-4 hover:bg-red-300 rounded-xl;
}
</style>
