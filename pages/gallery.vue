<template>
    <div>
      <!-- Gallery -->
      <main class="py-16 bg-gray-100 min-h-screen">
        <h1 class="text-4xl font-bold text-gray-800 mb-12 text-center">Gallery</h1>
        <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4 px-4">
          <div
            v-for="(image, index) in images"
            :key="index"
            class="relative overflow-hidden rounded-lg shadow-lg bg-white opacity-0"
            ref="galleryItems"
          >
            <img
              :src="image"
              alt="Gallery Image"
              class="w-full h-full object-cover transform transition-transform duration-300 hover:scale-105"
            />
            <div class="absolute inset-0 bg-black bg-opacity-40 opacity-0 hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
              <span class="text-white text-lg font-bold">View Image</span>
            </div>
          </div>
        </div>
      </main>
    </div>
  </template>
  
  <script setup>
  import { onMounted, ref } from 'vue';
  import gsap from 'gsap';
  
  const images = [
    '/images/foto1.avif',
    '/images/foto2.avif',
    '/images/foto3.avif',
    '/images/foto4.avif',
    '/images/foto5.avif',
    '/images/foto6.avif',
  ];
  
  const galleryItems = ref([]);
  
  onMounted(() => {
    gsap.fromTo(
      galleryItems.value,
      { opacity: 0, y: 20 },
      { opacity: 1, y: 0, stagger: 0.1, duration: 1 }
    );
  });
  </script>
  
  <style scoped>
  /* Add the Tailwind @apply directive to add animations */
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');
  
  body {
    font-family: 'Inter', sans-serif;
  }
  
  /* Keyframes for fade-in effect */
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  
  .animate-fade-in {
    animation: fadeIn 1s ease-in;
  }
  </style>
  