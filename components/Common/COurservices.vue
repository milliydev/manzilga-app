<template>
  <div class="text-center mt-24">
    <h1 class="text-blue-400">OUR SERVICES</h1>
    <h1 class="text-5xl py-10 font-bold">Custom IT Solutions for Your <br> Successful Business</h1>
  </div>

  <div data-aos="fade-up" class="grid grid-cols-1 sm:grid-cols-2 px-20 lg:grid-cols-3 gap-6 mt-14 justify-items-center">
    <div
        v-for="(service, index) in services"
        :key="index"
        class="flex flex-col px-4 py-6 rounded-lg w-[372px] h-[301px] justify-center bg-sky-100 text-black hover:text-white hover:bg-blue-700 transform duration-500 items-center text-center"
    >
      <div class="bg-blue-700 flex justify-center items-center rotate-45 w-[68px] h-[67px]">
        <img v-if="service.image" class="-rotate-45 w-10 h-10" :src="service.image" alt="Service Icon" />
      </div>
      <p class="py-6 text-2xl font-bold">{{ service.title }}</p>
      <p>{{ service.description }}</p>
    </div>

    <div class="flex flex-col px-4 py-6 rounded-lg w-[372px] h-[301px] justify-center bg-sky-100 text-black hover:text-white hover:bg-blue-700 transform duration-500 items-center text-center">
      <p class="text-2xl font-bold">Call Us For Quote</p>
      <p class="text-sm mt-2">
        Need help? Request a quote by contacting us directly. Our team is ready to support your project with custom solutions tailored to your needs.
      </p>
      <h1 class="py-6 text-3xl font-bold">+91 1234567890</h1>
    </div>
  </div>
</template>

<script setup>
const services = [
  {
    title: 'Cyber Security',
    image: '/images/security.svg',
    description: 'Cybersecurity refers to the practice of protecting computer systems, networks, and digital data from theft, damage, or unauthorized access.'
  },
  {
    title: 'Data Analytics',
    image: '/images/analystic.svg',
    description: 'Data analytics is the process of examining, cleaning, transforming, and interpreting data to discover meaningful insights, patterns, and trends.'
  },
  {
    title: 'Web Development',
    image: '/images/web.svg',
    description: 'Web development is the process of creating and maintaining websites or web applications using a combination of skills and technologies.'
  },
  {
    title: 'App Development',
    image: '/images/security.svg',
    description: 'App development focuses on creating software applications that run on mobile devices or other platforms to meet specific user needs.'
  },
  {
    title: 'SEO Optimization',
    image: '/images/analystic.svg',
    description: 'SEO improves the visibility and ranking of a website in search engine results, increasing organic traffic through optimized content and structure.'
  }
];
</script>

<style scoped>
img {
  width: 40px;
  height: 40px;
}
</style>