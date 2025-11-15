<template>
  <div class="max-w-7xl mx-auto mt-4 p-6">
    <div data-aos="fade-left" class="flex flex-col md:flex-row gap-6">
      <div class="md:w-1/2 p-6 bg-gray-100 h-[500px] py-24 rounded-lg shadow-md">
        <h2 class="text-3xl font-bold text-black mb-4">Need A Free Quote? Please Feel Free to Contact Us</h2>
        <div  class="flex gap-7 items-center">
          <div v-for="(item, index) in contactItems.slice(0, 2)" :key="index" class="flex gap-9 items-center">
            <img :src="`/images/${item.icon}.png`" :alt="item.title" class="w-8 h-8" @error="handleImageError">
            <p class="text-gray-600 mb-2"><strong v-if="item.highlight">{{ item.title }}</strong></p>
          </div>
        </div>
        <p class="text-gray-600 mt-6">
          I'd be happy to provide you with a free quote! However, I'd need more information about what
          you're interested in, specific requirements, and any other relevant information, so I can assist you
          in generating an accurate quote.
        </p>
        <div class="flex items-center gap-9 mt-12">
          <div v-for="(item, index) in contactItems.slice(2, 3)" :key="index" class="bg-blue-700 rounded-lg flex justify-center items-center w-20 h-16">
            <img :src="`/images/${item.icon}.png`" :alt="item.title" class="w-10 h-10" @error="handleImageError">
          </div>
          <p class="text-gray-600 font-bold flex flex-col mb-2">
            {{ contactItems[2].title }} <strong class="text-blue-600 font-medium">{{ contactItems[2].phone }}</strong>
          </p>
        </div>
      </div>
      <form class="w-[600px] p-7 bg-blue-600 py-4 justify-center rounded-lg shadow-md flex flex-col gap-4" @submit.prevent="handleSubmit">
        <input v-model="form.name" type="text" placeholder="Your Name" class="p-2 py-5 rounded bg-blue-100 focus:outline-none focus:ring-2 focus:ring-blue-500" required>
        <input v-model="form.email" type="email" placeholder="Your Email" class="p-2 py-5 rounded bg-blue-100 focus:outline-none focus:ring-2 focus:ring-blue-500" :class="{ 'border-red-500': emailError }" @input="validateEmail" required>
        <select v-model="form.service" class="p-2 py-4 rounded bg-blue-100 focus:outline-none focus:ring-2 focus:ring-blue-500" required>
          <option value="" disabled>Select A Services</option>
          <option value="web">Web Development</option>
          <option value="design">Design</option>
          <option value="support">Support</option>
        </select>
        <textarea v-model="form.message" placeholder="Messages" class="p-2 py-4 rounded bg-blue-100 focus:outline-none focus:ring-2 focus:ring-blue-500 h-24" required></textarea>
        <button type="submit" class="p-2 bg-blue-800 text-white rounded transition-all duration-300 hover:bg-black focus:outline-none focus:ring-2 focus:ring-blue-500" :disabled="isSubmitting">
          {{ isSubmitting ? 'Submitting...' : 'Request A Quote' }}
        </button>
        <p v-if="emailError" class="text-red-500 text-sm mt-2">{{ emailError }}</p>
        <p v-if="submitError" class="text-red-500 text-sm mt-2">{{ submitError }}</p>
        <p v-if="submitSuccess" class="text-green-500 text-sm mt-2">Form submitted successfully! Check your Telegram.</p>
      </form>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  setup() {
    const form = ref({
      name: '',
      email: '',
      service: '',
      message: ''
    });

    const isSubmitting = ref(false);
    const emailError = ref('');
    const submitError = ref('');
    const submitSuccess = ref(false);

    const contactItems = ref([
      { title: 'Reply within 24 hours', icon: 'reply', highlight: true },
      { title: '24 hrs telephone support', icon: 'reply2', highlight: true },
      { title: 'Call to ask a Question:', icon: 'phonecall', highlight: false, phone: '+91 1234567890' }
    ]);

    const TELEGRAM_BOT_TOKEN = '7463755151:AAEGdRW2PrKVoW9JzqhuLb020T----nplVY'; // Sizning tokeningiz
    const TELEGRAM_CHAT_ID = '6402351958'; // Sizning foydalanuvchi IDingiz

    const validateEmail = () => {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!emailRegex.test(form.value.email)) {
        emailError.value = 'Please enter a valid email address.';
      } else {
        emailError.value = '';
      }
    };

    const handleImageError = (event) => {
      console.error('Image failed to load:', event.target.src);
      event.target.src = '/images/placeholder.png';
    };

    const handleSubmit = async () => {
      if (emailError.value) {
        submitError.value = 'Please fix the email error before submitting.';
        return;
      }

      isSubmitting.value = true;
      submitError.value = '';
      submitSuccess.value = false;

      const message = `
        New Quote Request:
        Name: ${form.value.name}
        Email: ${form.value.email}
        Service: ${form.value.service}
        Message: ${form.value.message}
      `;

      try {
        const response = await fetch(`https://api.telegram.org/bot${TELEGRAM_BOT_TOKEN}/sendMessage`, {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({
            chat_id: TELEGRAM_CHAT_ID,
            text: message
          })
        });

        if (!response.ok) throw new Error('Failed to send message to Telegram');
        submitSuccess.value = true;
        form.value = { name: '', email: '', service: '', message: '' };
      } catch (error) {
        submitError.value = 'Error sending to Telegram. Please try again later.';
        console.error('Telegram API Error:', error);
      } finally {
        isSubmitting.value = false;
      }
    };

    onMounted(() => {
      console.log('Component mounted');
    });

    return { form, isSubmitting, emailError, submitError, submitSuccess, contactItems, validateEmail, handleImageError, handleSubmit };
  }
};
</script>