<template>
  <div class="mt-10 px-6 md:px-20 bg-gray-200">
    <div class="text-center mb-16">
      <p class="text-blue-600 font-bold text-sm tracking-wide">TEAM MEMBERS</p>
      <h1 class="font-extrabold text-4xl mt-2 text-gray-800">
        Professional Stuffs Ready to <br class="hidden md:block" />
        Help Your Business
      </h1>
    </div>

    <ul data-aos="fade-right" class="grid grid-cols-1 sm:grid-cols-2 gap-10">
      <li
          v-for="(team, index) in teams"
          :key="index"
          class="bg-white h-[200px] w-full rounded-2xl   shadow-md hover:shadow-xl transition duration-300 hover:scale-[1.03]"
      >
        <div class="flex gap-2 p-4">
          <img
              :src="team.image"
              :alt="`Photo of ${team.title}`"
              loading="lazy"
              class="w-[200px] h-[200px] translate-x-[-36px] rounded-2xl object-cover grayscale translate-y-[-2rem] hover:translate-x-[-21px] hover:translate-y-[-15px] hover:grayscale-0 transition duration-300"
              @error="handleImageError"
          />
          <div>
            <h2 class="text-xl font-bold text-blue-600">{{ team.title }}</h2>
            <p class="text-gray-700 font-medium mt-1">{{ team.description }}</p>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const teams = ref([
  { image: '/images/abbosaka.jpg', title: 'Zafur Uralov', description: 'Director of IT Academy, leading IT innovation and training initiatives.' },
  { image: '/images/ayubhon.jpg', title: 'Abdufattoh Jurayev', description: 'SMM mentor, helping businesses with social media strategies and online growth.' },

])

const handleImageError = (event) => {
  console.error('Image failed to load:', event.target.src)
  event.target.src = '/images/placeholder.png'
}
</script>

<style scoped>
</style>