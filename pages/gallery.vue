<template>
    <section class="py-10 bg-gray-50">
      <h2 class="text-3xl font-bold text-gray-800 mb-8 text-center">Image Gallery</h2>
      <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-4">
        <div
          v-for="(image, index) in images"
          :key="index"
          class="relative group overflow-hidden rounded-lg shadow-lg transform transition-transform duration-300 hover:scale-105"
        >
          <img
            :src="image"
            alt="Gallery Image"
            class="w-full h-full object-cover"
          />
          <div class="absolute inset-0 bg-black bg-opacity-50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
            <span class="text-white text-lg font-bold">View Image</span>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  const images = [
    '/images/foto1.avif',
    '/images/foto2.avif',
    '/images/foto3.avif',
    '/images/foto4.avif',
    '/images/foto5.avif',
    '/images/foto6.avif',
    ];
  </script>
  