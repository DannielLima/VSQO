<template>
    <div>
      <!-- Navbar -->
      <nav class="bg-gray-900 text-white py-4 shadow-md">
        <div class="container mx-auto flex justify-between items-center px-4">
          <a href="/" class="text-2xl font-bold">VSQO</a>
          <div>
            <a href="/" class="mx-4 hover:text-gray-400">Home</a>
            <a href="/gallery" class="mx-4 hover:text-gray-400">Gallery</a>
          </div>
        </div>
      </nav>
  
      <!-- Gallery -->
      <main class="py-10 bg-gray-100 min-h-screen">
        <h2 class="text-4xl font-bold text-gray-800 mb-8 text-center">Image Gallery</h2>
        <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4 px-4">
          <div
            v-for="(image, index) in images"
            :key="index"
            class="relative group overflow-hidden rounded-lg shadow-lg bg-white"
          >
            <img
              :src="image"
              alt="Gallery Image"
              class="w-full h-full object-cover transform transition-transform duration-300 group-hover:scale-105"
            />
            <div class="absolute inset-0 bg-black bg-opacity-40 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
              <span class="text-white text-lg font-bold">View Image</span>
            </div>
          </div>
        </div>
      </main>
  
      <!-- Footer -->
      <footer class="bg-gray-900 text-white py-4">
        <div class="container mx-auto text-center px-4">
          <p class="text-sm">&copy; 2024 VSQO. All rights reserved.</p>
        </div>
      </footer>
    </div>
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
  