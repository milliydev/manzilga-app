<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Top Contact Bar -->
    <div class="bg-slate-800 text-white py-2 px-4">
      <div class="container mx-auto flex justify-between items-center text-sm">
        <div class="flex items-center space-x-6">
          <div class="flex items-center space-x-2">
            <MapPin class="w-4 h-4" />
            <span>Toshkent city</span>
          </div>
          <div class="flex items-center space-x-2">
            <Phone class="w-4 h-4" />
            <span>+998 (97) 409 30 40</span>
          </div>
          <div class="flex items-center space-x-2">
            <Mail class="w-4 h-4" />
            <span>nexora.software@gmail.com</span>
          </div>
        </div>
        <div class="flex items-center space-x-3">
          <div class="flex space-x-2">
            <div class="w-8 h-8 bg-blue-600 rounded-full flex items-center justify-center cursor-pointer hover:bg-blue-700 transition-colors">
              <Facebook class="w-4 h-4" />
            </div>
            <div class="w-8 h-8 bg-blue-400 rounded-full flex items-center justify-center cursor-pointer hover:bg-blue-500 transition-colors">
              <Twitter class="w-4 h-4" />
            </div>
            <div class="w-8 h-8 bg-red-600 rounded-full flex items-center justify-center cursor-pointer hover:bg-red-700 transition-colors">
              <Youtube class="w-4 h-4" />
            </div>
            <div class="w-8 h-8 bg-blue-700 rounded-full flex items-center justify-center cursor-pointer hover:bg-blue-800 transition-colors">
              <Linkedin class="w-4 h-4" />
            </div>
            <div class="w-8 h-8 bg-gray-600 rounded-full flex items-center justify-center cursor-pointer hover:bg-gray-700 transition-colors">
              <Github class="w-4 h-4" />
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Navigation Header -->
    <nav class="text-white relative z-10 py-4 border-b px-4">
      <div class="container mx-auto flex justify-between items-center">
        <div class="flex items-center space-x-2">
          <div class="w-10 h-10 bg-blue-500 rounded-full flex items-center justify-center">
            <User class="w-6 h-6" />
          </div>
          <span class="text-xl font-bold">Nexora</span>
        </div>

        <div class="hidden md:flex items-center space-x-8 ">
          <a href="#" class="text-blue-400 hover:text-blue-300 transition-colors">Home</a>
          <a href="#" class="hover:text-blue-400 transition-colors">About Us</a>
          <a href="#" class="hover:text-blue-400 transition-colors">Services</a>
          <a href="#" class=" hover:text-blue-400 transition-colors">Blog</a>
          <a href="#" class="hover:text-blue-400 transition-colors">Pages</a>
          <a href="#" class="hover:text-blu e-400 transition-colors">Contact</a>
        </div>

        <div class="flex items-center space-x-4">
          <Search class="w-5 h-5 cursor-pointer hover:text-blue-400 transition-colors" />

        </div>

        <!-- Mobile Menu Button -->
        <button class="md:hidden">
          <Menu class="w-6 h-6" />
        </button>
      </div>
    </nav>
    <!-- Hero Section -->
    <div class=" min-h-screen">
      <img src="../../assets/images/bgimg.png" class="-mt-20 w-full"/>
      <div
          class="absolute inset-0 bg-cover bg-center bg-no-repeat"
          style="background-image: url('/placeholder.svg?height=800&width=1200')"
      ></div>
      <div class="absolute inset-0 ">
      </div>
      <!-- Hero Content -->
      <div class="z-10 absolute top-0 left-0 right-0 container mx-auto px-4 py-20">
        <div class="flex items-center justify-between min-h-[60vh]">
          <!-- Navigation Arrows -->
          <button class="text-white hover:text-blue-400 transition-colors">
            <ChevronLeft class="w-8 h-8" />
          </button>
          <!-- Main Content -->
          <div class="text-center text-white max-w-4xl relative  mx-auto">
            <p class="text-blue-400 text-lg mb-4 tracking-wider">CREATIVE & INNOVATIVE</p>
            <h1 class="text-5xl md:text-6xl font-bold mb-8 leading-tight">
              Creative & Innovative<br />
              <span class="text-blue-400">Digital Solution</span>
            </h1>

            <div class="flex flex-col sm:flex-row gap-4 justify-center items-center">
              <button class="bg-blue-500 hover:bg-blue-600 text-white px-8 py-3 rounded transition-colors font-semibold">
                Free Quote
              </button>
              <button class="border-2 border-white text-white hover:bg-white hover:text-slate-900 px-8 py-3 rounded transition-colors font-semibold">
                Free Quote
              </button>
            </div>
          </div>

          <!-- Navigation Arrows -->
          <button class="text-white hover:text-blue-400 transition-colors">
            <ChevronRight class="w-8 h-8" />
          </button>
        </div>
      </div>
    </div>

    <!-- Statistics Section -->
    <div class="bg-white py-0">
      <div class="container mx-auto px-4">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-0 -mt-16 relative z-20">
          <!-- Happy Clients -->
          <div class="bg-blue-500 text-white p-8 text-center">
            <div class="flex items-center justify-center mb-4">
              <Users class="w-12 h-12" />
            </div>
            <h3 class="text-lg font-semibold mb-2">Happy Clients</h3>
            <p class="text-3xl font-bold">12345</p>
          </div>

          <!-- Project Done -->
          <div class="bg-blue-600 text-white p-8 text-center">
            <div class="flex items-center justify-center mb-4">
              <CheckCircle class="w-12 h-12" />
            </div>
            <h3 class="text-lg font-semibold mb-2">Project Done</h3>
            <p class="text-3xl font-bold">12345</p>
          </div>

          <!-- Award Win -->
          <div class="bg-blue-500 text-white p-8 text-center">
            <div class="flex items-center justify-center mb-4">
              <Award class="w-12 h-12" />
            </div>
            <h3 class="text-lg font-semibold mb-2">Award Win</h3>
            <p class="text-3xl font-bold">12345</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<!--<script setup>-->
<!--import {-->
<!--  MapPin,-->
<!--  Phone,-->
<!--  Mail,-->
<!--  Facebook,-->
<!--  Twitter,-->
<!--  Youtube,-->
<!--  Linkedin,-->
<!--  Github,-->
<!--  User,-->
<!--  Search,-->
<!--  Menu,-->
<!--  ChevronLeft,-->
<!--  ChevronRight,-->
<!--  Users,-->
<!--  CheckCircle,-->
<!--  Award-->
<!--} from 'lucide-vue-next'-->
<!--</script>-->

<style scoped>
/* Additional custom styles if needed */
.container {
  max-width: 1200px;
}
</style>