<script setup>
import { LinkIcon, MapIcon, LibraryIcon, BookOpenIcon, ColorSwatchIcon, CalendarIcon } from '@heroicons/vue/outline'
import banner from '../assets/banner.svg'
import Wrapper from '../components/Wrapper.vue'
import { onSnapshot, doc } from 'firebase/firestore'
import { db } from '../firebase.js'
import state from '../model.js'
import { useRouter } from 'vue-router'
const router = useRouter()
let home = $ref({})

onSnapshot(doc(db, 'cache', 'home'), doc => home = doc.data() || {})
</script>

<template>
  <div class="relative w-full h-full flex flex-col justify-center pl-10 sm:pl-20 all-transition">
    <img class="absolute z-0 left-0 bottom-0 w-full" :src="banner">
    <div class="absolute top-0 left-0 w-full">
      <wrapper :show="home.top">
        <div class="bg-blue-200 text-blue-700 p-2 flex items-center justify-center" v-html="home.top" />
      </wrapper>
    </div>
    <h1 class="relative text-6xl font-bold text-gray-800">GoGaucho</h1>
    <div class="w-4/5 flex flex-wrap relative py-4">
      <button @click="router.push('/link')"><link-icon class="w-5 mr-2 text-gray-500" />Links</button>
      <button @click="router.push('/map')"><map-icon class="w-5 mr-2 text-gray-500" />Map</button>
      <button @click="router.push('/dining')"><color-swatch-icon class="w-6 mr-2 text-gray-500" />Dining Commons</button>
      <button @click="router.push('/waitz')"><library-icon class="w-6 mr-2 text-gray-500" />Building Capacity</button>
      <button @click="router.push('/course')"><book-open-icon class="w-6 mr-2 text-gray-500" />Course</button>
      <button @click="router.push('/class')"><calendar-icon class="w-6 mr-2 text-gray-500" />My Classes</button>
    </div>
  </div>
</template>

<style scoped>
button {
  transition: all 0.3s ease;
  @apply bg-white shadow-md hover:shadow-lg rounded px-3 py-2 m-2 flex items-center;
}
</style>