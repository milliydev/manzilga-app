<template>
  <section class="py-16 px-4 bg-gray-50">
    <div data-aos="fade-down

" class="max-w-6xl mx-auto">
      <!-- Header -->
      <div class="text-center mb-12">
        <div class="flex items-center justify-center mb-4">
          <div class="w-8 h-1 bg-gray-300 rounded"></div>
          <div class="w-12 h-1 bg-blue-500 rounded mx-2"></div>
          <div class="w-8 h-1 bg-gray-300 rounded"></div>
        </div>
        <p class="text-blue-500 font-semibold text-sm tracking-wider uppercase mb-2">
          TESTIMONIAL
        </p>
        <h2 class="text-3xl md:text-4xl font-bold text-gray-800 leading-tight">
          What Our Clients Say About<br>
          Our Digital Services
        </h2>
      </div>

      <!-- Testimonials Grid -->
      <div class="grid md:grid-cols-3 gap-8">
        <!-- Michael Anderson -->
        <div class="testimonial-card group">
          <div class="bg-white rounded-lg p-6 shadow-md transition-all duration-300 ease-in-out group-hover:shadow-2xl group-hover:scale-105 group-hover:-translate-y-2">
            <div class="flex items-center mb-4">
              <div class="w-12 h-12 bg-gray-300 rounded-full flex items-center justify-center mr-4">
                <svg class="w-6 h-6 text-gray-600" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 9a3 3 0 100-6 3 3 0 000 6zm-7 9a7 7 0 1114 0H3z" clip-rule="evenodd" />
                </svg>
              </div>
              <div>
                <h3 class="font-semibold text-gray-800">Michael Anderson</h3>
                <p class="text-blue-500 text-sm font-medium">PROFESSION</p>
              </div>
            </div>
            <p class="text-gray-600 text-sm leading-relaxed">
              The Information Technology (IT) field encompasses a wide range of professions and career opportunities. IT professionals work with technology systems and infrastructure to support various business operations and various aspects of computing and information systems.
            </p>
          </div>
        </div>

        <!-- Emily Davis -->
        <div class="testimonial-card group">
          <div class="bg-white rounded-lg p-6 shadow-md transition-all duration-300 ease-in-out group-hover:shadow-2xl group-hover:scale-105 group-hover:-translate-y-2">
            <div class="flex items-center mb-4">
              <div class="w-12 h-12 bg-gray-300 rounded-full flex items-center justify-center mr-4">
                <svg class="w-6 h-6 text-gray-600" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 9a3 3 0 100-6 3 3 0 000 6zm-7 9a7 7 0 1114 0H3z" clip-rule="evenodd" />
                </svg>
              </div>
              <div>
                <h3 class="font-semibold text-gray-800">Emily Davis</h3>
                <p class="text-blue-500 text-sm font-medium">BUSINESS WOMAN</p>
              </div>
            </div>
            <p class="text-gray-600 text-sm leading-relaxed">
              Business women refers to women who are actively engaged in various aspects of the business world. This can include women who are entrepreneurs, executives, managers, consultants, or other professionals, or employees in various industries.
            </p>
          </div>
        </div>

        <!-- James Wilson -->
        <div class="testimonial-card group">
          <div class="bg-white rounded-lg p-6 shadow-md transition-all duration-300 ease-in-out group-hover:shadow-2xl group-hover:scale-105 group-hover:-translate-y-2">
            <div class="flex items-center mb-4">
              <div class="w-12 h-12 bg-gray-300 rounded-full flex items-center justify-center mr-4">
                <svg class="w-6 h-6 text-gray-600" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 9a3 3 0 100-6 3 3 0 000 6zm-7 9a7 7 0 1114 0H3z" clip-rule="evenodd" />
                </svg>
              </div>
              <div>
                <h3 class="font-semibold text-gray-800">James Wilson</h3>
                <p class="text-blue-500 text-sm font-medium">APPLICATION DEVELOPMENT</p>
              </div>
            </div>
            <p class="text-gray-600 text-sm leading-relaxed">
              Application development refers to the process of creating software applications for various platforms and devices, such as mobile phones, desktop computers, web browsers, and other digital platforms.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.testimonial-card {
  cursor: pointer;
}

.testimonial-card:hover .bg-white {
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}

/* Additional smooth transitions */
.testimonial-card .bg-white {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

/* Hover effect for the entire card */
@media (hover: hover) {
  .testimonial-card:hover {
    z-index: 10;
  }
}
</style>