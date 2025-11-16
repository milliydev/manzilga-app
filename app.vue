<template>
  <div class="min-h-screen bg-[#f1f5f9]">
    <!-- NAVBAR -->
    <nav class="w-full flex items-center justify-between px-6 md:px-12 py-4 bg-white shadow-md">
      <div class="flex items-center gap-3">
        <h1 class="text-2xl font-extrabold text-[#007bff]">Manzilga</h1>
      </div>

      <div class="hidden md:flex gap-8 text-[18px] font-semibold text-[#1b1b1b]">
        <a href="#">Biz haqimizda</a>
        <a href="#">Savol / Javob</a>
        <a href="#">Chipta tiklash</a>
      </div>
    </nav>

    <!-- HERO + FORM -->
    <div class="w-full flex flex-col items-center mt-12 px-4 pb-12">
      <h2 class="text-3xl md:text-5xl font-bold text-[#1b1b1b] text-center">
        Har kuni O'zbekiston bo'ylab mashina qatnovi
      </h2>

      <div class="w-full max-w-6xl bg-white mt-10 rounded-2xl p-6 grid grid-cols-1 md:grid-cols-4 gap-4 shadow-xl">
        <select v-model="from" class="p-4 rounded-xl border outline-none w-full bg-white">
          <option value="">Qayerdan</option>
          <option v-for="r in regions" :key="r">{{ r }}</option>
        </select>

        <select v-model="to" class="p-4 rounded-xl border outline-none w-full bg-white">
          <option value="">Qayerga</option>
          <option v-for="r in regions" :key="r">{{ r }}</option>
        </select>

        <input type="date" class="p-4 rounded-xl border outline-none w-full bg-white" v-model="date" />

        <button
            @click="openCarsModal"
            class="p-4 rounded-xl bg-[#007bff] text-white font-bold hover:bg-[#0063d1] transition"
        >
          Qidiruvni boshlash
        </button>
      </div>

      <div v-if="price" class="mt-6 bg-white shadow-xl px-10 py-4 rounded-xl text-2xl font-bold text-[#007bff]">
        Narx: {{ price.toLocaleString() }} so’m
      </div>
    </div>

    <!-- ====== CARS MODAL (90% ekran) ====== -->
    <div v-if="showCarsModal" class="fixed inset-0 z-50 flex items-center justify-center">
      <!-- backdrop -->
      <div class="absolute inset-0 bg-black/60" @click="closeAll"></div>

      <!-- modal box - 90% of viewport -->
      <div
          class="relative bg-white rounded-2xl shadow-2xl w-[90vw] h-[90vh] overflow-hidden flex flex-col"
          role="dialog"
          aria-modal="true"
      >
        <!-- header -->
        <div class="flex items-center justify-between px-4 md:px-8 py-3 border-b">
          <div class="flex items-center gap-3">
            <button @click="closeAll" class="p-2 rounded-full hover:bg-gray-100">
              <!-- X button -->
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-700" fill="none" viewBox="0 0 24 24"
                   stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12"/>
              </svg>
            </button>
            <div>
              <h3 class="text-lg md:text-xl font-bold text-[#007bff]">Mashinalar — {{ from || "Barcha" }} → {{ to || "Barcha" }}</h3>
              <p class="text-sm text-gray-500">Sana: {{ date || "tayinlanmagan" }}</p>
            </div>
          </div>

          <div class="flex items-center gap-3">
            <div class="text-sm text-gray-600">Topilgan: {{ filteredCars.length }}</div>
            <button @click="closeAll" class="px-3 py-2 bg-red-500 text-white rounded-xl">Yopish</button>
          </div>
        </div>

        <!-- body: two-column layout on md+, single column on mobile -->
        <div class="flex-1 flex overflow-hidden">
          <!-- left: list -->
          <div class="w-full md:w-2/3 h-full overflow-auto p-4">
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
              <template v-for="car in filteredCars" :key="car.id">
                <div
                    class="bg-white rounded-xl border shadow-sm hover:shadow-md cursor-pointer overflow-hidden flex flex-col"
                    @click="openCarDetail(car)"
                >
                  <div class="relative h-40 md:h-36 w-full">
                    <!-- remote placeholder images (picsum) -->
                    <img
                        :src="car.image"
                        alt="car image"
                        class="object-cover w-full h-full"
                        loading="lazy"
                    />
                    <div class="absolute left-3 top-3 bg-white/90 px-2 py-1 rounded-md text-xs font-semibold">
                      {{ car.make }} · {{ car.model }}
                    </div>
                    <div class="absolute right-3 bottom-3 bg-white border-4 rounded-2xl border-black text-black px-4 py-1 rounded-md text-sm font-semibold">
                      {{ car.plate }}
                    </div>
                  </div>

                  <div class="p-3 flex-1 flex flex-col justify-between">
                    <div>
                      <div class="flex items-center justify-between">
                        <div class="text-sm text-gray-600">{{ car.transmission }} · {{ car.year }}</div>
                        <div class="text-sm text-[#007bff] font-bold">{{ car.price.toLocaleString() }} so'm</div>
                      </div>
                      <p class="mt-2 text-sm text-gray-700 line-clamp-2">{{ car.description }}</p>
                    </div>

                    <div class="mt-3 flex items-center justify-between">
                      <div class="text-xs text-gray-500">Haydovchi: {{ car.driver.name }}</div>
                      <div class="text-xs text-gray-500">Yosh: {{ car.driver.age }}</div>
                    </div>
                  </div>
                </div>
              </template>
            </div>
          </div>

          <!-- right: detail panel (like a page). On small screens it becomes an overlay full height) -->
          <!-- right: detail panel -->
          <transition name="slide-fade" mode="out-in">
            <div
                v-if="selectedCar"
                class="w-full md:w-[40%] h-full bg-white shadow-xl rounded-xl p-6 overflow-y-auto fixed md:static top-0 right-0 z-50"
                key="detail"
            >
              <!-- CLOSE BTN -->
              <button
                  @click="selectedCar = null"
                  class="absolute top-4 right-4 text-gray-600 hover:text-black text-2xl"
              >
                ✕
              </button>

              <h2 class="text-3xl font-bold mb-3">
                {{ selectedCar.name }}
              </h2>

              <img
                  :src="selectedCar.image"
                  class="w-full h-52 object-cover rounded-xl mb-4"
              />

              <p class="text-lg font-semibold">Raqam: {{ selectedCar.number }}</p>
              <p class="mt-2 text-gray-700">Haydovchi: {{ selectedCar.driver.name }}</p>
              <p class="text-gray-700">Yoshi: {{ selectedCar.driver.age }}</p>
              <p class="text-gray-700">Jinsi: {{ selectedCar.driver.gender }}</p>
            </div>
          </transition>

        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

import treckerimg from '/public/images/trecker.png'
/**
 * carsJson — barcha mashina ma'lumotlari shu yerda JSON formatida saqlangan.
 * Siz xohlasangiz bu obyektni tashqi faylga ham eksport qilib,
 * yoki API orqali yuklab ishlatishingiz mumkin.
 */
const carsJson = [
  {
    id: 1,
    make: "",
    model: "trecker 2",
    year: 2015,
    transmission: "Mexanika",
    price: 100000,
    plate: "70 F 614 ZA",
    description: "Tezkor va arzon — qisqa masofalar uchun ideal.",
    image: treckerimg,
    driver: { name: "Zohid", age: 20, gender: "Erkak", phone: "+998974093040", rating: 4.6 },
    from: "Toshkent",
    to: "Samarqand"
  },
  {
    id: 2,
    make: "Chevrolet",
    model: "Cobalt",
    year: 2018,
    transmission: "Avtomat",
    price: 120000,
    plate: "10 B 456 BB",
    description: "Yaxshi konditsioner va qulay o‘rindiqlar.",
    image: "https://picsum.photos/seed/2/800/500",
    driver: { name: "Dilshod", age: 29, gender: "Erkak", phone: "+998931112233", rating: 4.8 },
    from: "Toshkent",
    to: "Buxoro"
  },
  {
    id: 3,
    make: "Ravon",
    model: "Gentra",
    year: 2017,
    transmission: "Mexanika",
    price: 130000,
    plate: "33 C 789 CC",
    description: "Iqtisodiy, ishonchli va o‘rta sig‘imli.",
    image: "https://picsum.photos/seed/3/800/500",
    driver: { name: "Malika", age: 27, gender: "Ayol", phone: "+998901112233", rating: 4.9 },
    from: "Namangan",
    to: "Farg'ona"
  },
  {
    id: 4,
    make: "Spark",
    model: "Spark",
    year: 2016,
    transmission: "Avtomat",
    price: 105000,
    plate: "15 D 001 DD",
    description: "Shahar ichida qulay va ixcham.",
    image: "https://picsum.photos/seed/4/800/500",
    driver: { name: "Rustam", age: 41, gender: "Erkak", phone: "+998977665544", rating: 4.5 },
    from: "Toshkent",
    to: "Jizzax"
  },
  {
    id: 5,
    make: "Nexia",
    model: "Nexia 3",
    year: 2019,
    transmission: "Mexanika",
    price: 115000,
    plate: "20 E 222 EE",
    description: "Ishonchli, servis oson, yoqilg‘i tejamkor.",
    image: "https://picsum.photos/seed/5/800/500",
    driver: { name: "Oybek", age: 36, gender: "Erkak", phone: "+998994443322", rating: 4.7 },
    from: "Andijon",
    to: "Namangan"
  },
  {
    id: 6,
    make: "Spark",
    model: "Spark 1.2",
    year: 2020,
    transmission: "Avtomat",
    price: 125000,
    plate: "70 F 333 FF",
    description: "Yangi va toza mashina, konditsioner bilan.",
    image: "https://picsum.photos/seed/6/800/500",
    driver: { name: "Gulnora", age: 30, gender: "Ayol", phone: "+998901223344", rating: 4.85 },
    from: "Sirdaryo",
    to: "Toshkent"
  },
  {
    id: 7,
    make: "Hyundai",
    model: "Accent",
    year: 2014,
    transmission: "Mexanika",
    price: 110000,
    plate: "44 G 444 GG",
    description: "Qulay orindiqlar, o‘rta yo‘l turlari uchun mos.",
    image: "https://picsum.photos/seed/7/800/500",
    driver: { name: "Sardor", age: 45, gender: "Erkak", phone: "+998901998877", rating: 4.3 },
    from: "Qarshi",
    to: "Surxondaryo"
  },
  {
    id: 8,
    make: "Lacetti",
    model: "Lacetti",
    year: 2013,
    transmission: "Mexanika",
    price: 98000,
    plate: "55 H 555 HH",
    description: "Arzon va ishonchli — qisqa yo‘llar uchun.",
    image: "https://picsum.photos/seed/8/800/500",
    driver: { name: "Nilufar", age: 32, gender: "Ayol", phone: "+998909009009", rating: 4.4 },
    from: "Navoiy",
    to: "Buxoro"
  },
  {
    id: 9,
    make: "Damas",
    model: "Damas 1.2",
    year: 2012,
    transmission: "Mexanika",
    price: 92000,
    plate: "66 I 666 II",
    description: "Oddiy va samarali — byudjet variant.",
    image: "https://picsum.photos/seed/9/800/500",
    driver: { name: "Aziz", age: 39, gender: "Erkak", phone: "+998906006006", rating: 4.2 },
    from: "Toshkent",
    to: "Samarqand"
  },
  {
    id: 10,
    make: "Kaptiva",
    model: "Kaptiva",
    year: 2011,
    transmission: "Avtomat",
    price: 140000,
    plate: "77 J 777 JJ",
    description: "Katta yuk sig‘imi va yo‘lovchi joyi.",
    image: "https://picsum.photos/seed/10/800/500",
    driver: { name: "Bobur", age: 50, gender: "Erkak", phone: "+998901010101", rating: 4.1 },
    from: "Farg'ona",
    to: "Namangan"
  },
  {
    id: 11,
    make: "Tracker",
    model: "Tracker",
    year: 2019,
    transmission: "Avtomat",
    price: 150000,
    plate: "88 K 888 KK",
    description: "Off-road imkoniyati va qulay salon.",
    image: "https://picsum.photos/seed/11/800/500",
    driver: { name: "Elmira", age: 28, gender: "Ayol", phone: "+998905005005", rating: 4.9 },
    from: "Xorazm",
    to: "Navoiy"
  },
  {
    id: 12,
    make: "Cobalt",
    model: "Cobalt 1.5",
    year: 2021,
    transmission: "Avtomat",
    price: 160000,
    plate: "99 L 999 LL",
    description: "Eng yangi model, zamonaviy o‘rindiqlar va xavfsizlik.",
    image: "https://picsum.photos/seed/12/800/500",
    driver: { name: "Shahlo", age: 35, gender: "Ayol", phone: "+998903003003", rating: 5.0 },
    from: "Toshkent",
    to: "Andijon"
  }
]

/* FORM state */
const from = ref("")
const to = ref("")
const date = ref("")
const price = ref(null)
const showCarsModal = ref(false)
const selectedCar = ref(null)

/* regions for selects */
const regions = [
  "Toshkent","Samarqand","Buxoro","Jizzax","Qarshi","Navoiy","Andijon",
  "Namangan","Farg'ona","Xorazm","Surxondaryo","Sirdaryo"
]

/* helpers */
const isMobile = computed(() => window.innerWidth < 768)

/* simple price calculator (demo) */
const calculatePrice = () => {
  price.value = Math.floor(Math.random() * 40000) + 100000
}

/* open modal and show list */
const openCarsModal = () => {
  if (!from.value && !to.value) {
    // allow opening even without selection, but set price randomly
    calculatePrice()
  } else {
    calculatePrice()
  }
  showCarsModal.value = true
}

/* close everything */
const closeAll = () => {
  showCarsModal.value = false
  selectedCar.value = null
}

/* open detail view for a car */
const openCarDetail = (car) => {
  selectedCar.value = car
}

/* computed: filter by from/to if provided */
const filteredCars = computed(() => {
  return carsJson.filter(c => {
    const fromOk = from.value ? c.from === from.value : true
    const toOk = to.value ? c.to === to.value : true
    return fromOk && toOk
  })
})

/* expose to template (script setup auto exposes refs) */
</script>

<style>
/* optional transitions */
.slide-fade-enter-active {
  transition: all 250ms ease;
}
.slide-fade-leave-active {
  transition: all 200ms ease;
}
.slide-fade-enter-from {
  transform: translateX(10px);
  opacity: 0;
}
.slide-fade-enter-to {
  transform: translateX(0);
  opacity: 1;
}
.slide-fade-leave-from {
  transform: translateX(0);
  opacity: 1;
}
.slide-fade-leave-to {
  transform: translateX(10px);
  opacity: 0;
}

/* small helpers for text clamping (if using tailwind plugin you can replace) */
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>
