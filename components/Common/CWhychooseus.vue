<template>
  <div class="bg-white py-10 px-6">
    <p class="text-center text-blue-500 text-lg font-semibold">WHY CHOOSE US</p>
    <h1 class="text-center text-4xl font-bold text-gray-800 mt-2">
      We Are Here to Grow Your <br />
      Business Exponentially
    </h1>


    <div data-aos="zoom-in-up" class="flex  flex-wrap justify-center mt-10 gap-10">
      <div class="flex flex-col gap-10">
        <div
            v-for="(choose, index) in chooses.slice(0, 2)"
            :key="'left-' + index"
            class="flex items-center justify-center gap-4 max-w-sm min-h-[190px] bg-white rounded-lg p-4 shadow-md hover:shadow-xl transition-shadow duration-300"
        >
          <div
              class="bg-blue-500 w-64 h-24 flex justify-center items-center rounded hover:bg-blue-600 transition duration-300"
          >
            <img :src="choose.image" alt="icon" class="w-8 h-8" />
          </div>
          <div>
            <h2 class="text-lg font-bold text-gray-800">{{ choose.title }}</h2>
            <p class="text-sm text-gray-600 mt-1">{{ choose.description }}</p>
          </div>
        </div>
      </div>

      <div>
        <img
            src="/images/retangle.png "
            alt="Main"
            class="w-[298px] h-[418px] hover:scale-105 transition-all duration-500 rounded shadow-md object-cover"
        />
      </div>

      <div class="flex flex-col gap-10">
        <div
            v-for="(choose, index) in chooses.slice(2, 4)"
            :key="'right-' + index"
            class="flex items-center gap-4 max-w-sm min-h-[190px] bg-white rounded-lg p-4 shadow-md hover:shadow-xl transition-shadow duration-300"
        >
          <div
              class="bg-blue-500 w-64 h-24  flex justify-center items-center rounded hover:bg-blue-600 transition duration-300"
          >
            <img :src="choose.image" alt="icon" class="w-8 h-8" />
          </div>
          <div>
            <h2 class="text-lg font-bold text-gray-800">{{ choose.title }}</h2>
            <p class="text-sm text-gray-600 mt-1">{{ choose.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const chooses = [
  {
    image: '/images/compseting.svg',
    title: 'Best In Industry',
    description: '“Best in Industry” is a term used to describe a company, product, or service that is considered the top performer within a particular industry.',
  },
  {
    image: '/images/compseting.svg',
    title: 'Award Winning',
    description: 'Award winning refers to recognition for excellence in a particular field or category by an established organization or committee.',
  },
  {
    image: '/images/compseting.svg',
    title: 'Proffesonal Staff',
    description: 'Professional staff refers to skilled individuals who operate within a business or organization with competence and expertise.',
  },
  {
    image: '/images/compseting.svg',
    title: '24/7 Support',
    description: '24/7 support means service or assistance is available at any time, day or night, throughout the week.',
  },
];
</script>
