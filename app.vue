<template>
  <div class="min-h-screen bg-[#f1f5f9]">
    <!-- NAVBAR -->
    <nav class="w-full flex items-center justify-between px-6 md:px-12 py-4 bg-white shadow-md">
      <div class="flex items-center gap-3">
<!--        <img src="/car-logo.png" class="w-10 h-10" alt="logo" />-->
        <h1 class="text-2xl font-extrabold texte-[#007bff]">Manzilga</h1>
      </div>

      <div class="hidden md:flex gap-8 text-[18px] font-semibold text-[#1b1b1b]">
        <a href="#">Biz haqimizda</a>
        <a href="#">Savol / Javob</a>
        <a href="#">Chipta tiklash</a>
      </div>
    </nav>

    <!-- HERO + FORM -->
    <div class="w-full flex flex-col items-center mt-12 px-4">
      <h2 class="text-3xl md:text-5xl font-bold text-[#1b1b1b] text-center">
        Har kuni O'zbekiston bo'ylab mashina qatnovi
      </h2>

      <div
          class="w-full max-w-6xl bg-white mt-10 rounded-2xl p-6 grid grid-cols-1 md:grid-cols-4 gap-4 shadow-xl"
      >
        <!-- From -->
        <select v-model="from" class="p-4 rounded-xl border outline-none w-full bg-white">
          <option value="">Qayerdan</option>
          <option v-for="r in regions" :key="r">{{ r }}</option>
        </select>

        <!-- To -->
        <select v-model="to" class="p-4 rounded-xl border outline-none w-full bg-white">
          <option value="">Qayerga</option>
          <option v-for="r in regions" :key="r">{{ r }}</option>
        </select>

        <!-- Date -->
        <input
            type="date"
            class="p-4 rounded-xl border outline-none w-full bg-white"
            v-model="date"
        />

        <!-- Search Button -->
        <button
            @click="calculatePrice"
            class="p-4 rounded-xl bg-[#007bff] text-white font-bold hover:bg-[#0063d1] transition"
        >
          Qidiruvni boshlash
        </button>
      </div>

      <!-- PRICE BOX -->
      <div
          v-if="price"
          class="mt-6 bg-white shadow-xl px-10 py-4 rounded-xl text-2xl font-bold text-[#007bff]"
      >
        Narx: {{ price.toLocaleString() }} so’m
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const from = ref("");
const to = ref("");
const date = ref("");
const price = ref(null);

const regions = [
  "Toshkent","Samarqand","Buxoro","Jizzax","Qarshi","Navoiy","Andijon",
  "Namangan","Farg'ona","Xorazm","Surxondaryo","Sirdaryo"
];

const calculatePrice = () => {
  if (from.value && to.value) {
    price.value = Math.floor(Math.random() * 40000) + 100000; // 100k - 140k
  }
};
</script>

<style>
body {
  font-family: "Manrope", sans-serif;
}
</style>
