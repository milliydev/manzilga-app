<template>
  <section class="py-12 px-4">
    <div class="max-w-7xl mx-auto">
      <!-- Optional heading -->
      <div class="text-center mb-8">
        <h3 class="text-lg font-semibold text-gray-600 mb-6">
          Trusted by leading companies worldwide
        </h3>
      </div>

      <!-- Logos Container -->
      <div class="flex flex-wrap items-center justify-center gap-8 md:gap-12 lg:gap-16">
        <div
            v-for="company in companies"
            :key="company.name"
            class="flex items-center justify-center opacity-70 hover:opacity-100 transition-opacity duration-300 cursor-pointer"
        >
          <img
              :src="company.logo"
              :alt="company.name + ' logo'"
              class="h-8 md:h-10 lg:h-12 w-auto object-contain filter grayscale hover:grayscale-0 transition-all duration-300"
          >
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import googleLogo from '../../assets/images/google.svg';


const companies = [
  {
    name: 'Google',
    logo: googleLogo,
  },
  {
    name: 'Apple',
    logo: googleLogo,
  },
  {
    name: 'Microsoft',
    logo: googleLogo,
  },
  {
    name: 'IBM',
    logo: googleLogo,
  },
  {
    name: 'Yahoo!',
    logo: googleLogo,
  },
  {
    name: 'Dell',
    logo: googleLogo,
  }
]
</script>

<style scoped>
/* Additional custom styles if needed */
.company-logo {
  max-height: 48px;
  width: auto;
}

@media (max-width: 768px) {
  .company-logo {
    max-height: 32px;
  }
}
</style>