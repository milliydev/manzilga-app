<template>
  <footer class="bg-slate-900 text-white mt-40">
    <div class="container mx-auto px-4 py-12">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">

        <!-- Company Info Section -->
        <div class="bg-blue-500 p-4 rounded-lg">
          <div class="flex items-center space-x-2 mb-4">
            <div class="w-8 h-8 bg-white rounded-full flex items-center justify-center">
              <User class="w-5 h-5 text-blue-500" />
            </div>
            <h3 class="text-xl font-bold">Infosys</h3>
          </div>
          <p class="text-sm mb-6 leading-relaxed">
            I'd be happy to provide you with information about an IT company.
            However, I would need more specific details or the name of the
            company you have in mind to provide you with accurate information.
          </p>
          <div class="flex w-10">
            <input
                v-model="email"
                type="email"
                placeholder="Enter Your Email"
                class="flex-1  py-2 text-gray-800 rounded-l focus:outline-none focus:ring-2 focus:ring-blue-300"
            />
            <button
                @click="signUp"
                class="bg-slate-800 hover:bg-slate-700 px-4 py-2 rounded-r transition-colors font-semibold"
            >
              Sign Up
            </button>
          </div>
        </div>

        <!-- Get to Touch Section -->
        <div>
          <h3 class="text-lg font-semibold mb-6">Get to Touch</h3>
          <div class="space-y-4">
            <div class="flex items-start space-x-3">
              <MapPin class="w-5 h-5 text-blue-400 mt-1 flex-shrink-0" />
              <span class="text-sm">135 Street,new york,USA</span>
            </div>

            <div class="flex items-center space-x-3">
              <Mail class="w-5 h-5 text-blue-400 flex-shrink-0" />
              <span class="text-sm">xyz@gmail.com</span>
            </div>

            <div class="flex items-center space-x-3">
              <Phone class="w-5 h-5 text-blue-400 flex-shrink-0" />
              <span class="text-sm">+91 1111111111</span>
            </div>
          </div>

          <!-- Social Media Icons -->
          <div class="flex space-x-3 mt-6">
            <div class="w-8 h-8 bg-blue-400 rounded flex items-center justify-center cursor-pointer hover:bg-blue-500 transition-colors">
              <Twitter class="w-4 h-4" />
            </div>
            <div class="w-8 h-8 bg-blue-600 rounded flex items-center justify-center cursor-pointer hover:bg-blue-700 transition-colors">
              <Facebook class="w-4 h-4" />
            </div>
            <div class="w-8 h-8 bg-blue-700 rounded flex items-center justify-center cursor-pointer hover:bg-blue-800 transition-colors">
              <Linkedin class="w-4 h-4" />
            </div>
            <div class="w-8 h-8 bg-pink-500 rounded flex items-center justify-center cursor-pointer hover:bg-pink-600 transition-colors">
              <Instagram class="w-4 h-4" />
            </div>
          </div>
        </div>

        <!-- Quick Links Section -->
        <div>
          <h3 class="text-lg font-semibold mb-6">Quick Links</h3>
          <ul class="space-y-3">
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>Home</span>
              </a>
            </li>
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>About Us</span>
              </a>
            </li>
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>Our Services</span>
              </a>
            </li>
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>Meet The Team</span>
              </a>
            </li>
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>Latest Blog</span>
              </a>
            </li>
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>Contact Us</span>
              </a>
            </li>
          </ul>
        </div>

        <!-- Popular Links Section -->
        <div>
          <h3 class="text-lg font-semibold mb-6">Popular Links</h3>
          <ul class="space-y-3">
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>Home</span>
              </a>
            </li>
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>About Us</span>
              </a>
            </li>
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>Our Services</span>
              </a>
            </li>
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>Meet The Team</span>
              </a>
            </li>
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>Latest Blog</span>
              </a>
            </li>
            <li>
              <a href="#" class="flex items-center space-x-2 text-sm hover:text-blue-400 transition-colors">
                <ChevronRight class="w-4 h-4 text-blue-400" />
                <span>Contact Us</span>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>

    <!-- Copyright Section -->
    <div class="border-t border-slate-700 py-4">
      <div class="container mx-auto px-4">
        <p class="text-center text-sm text-gray-400">
          © IT Agency Website. All Rights Reserved. Designed by
          <span class="text-blue-400 hover:text-blue-300 cursor-pointer">Jay Dhimaliya</span>
        </p>
      </div>
    </div>
  </footer>
</template>



<style scoped>
.container {
  max-width: 1200px;
}
</style>