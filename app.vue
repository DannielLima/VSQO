<template>
  <div>
    <nav class="bg-white text-gray-800 py-4 shadow-md border-b border-gray-200">
      <div class="container mx-auto flex justify-between items-center px-6">
        <a href="/" class="text-3xl font-semibold">VSQO</a>
        <div class="space-x-4">
          <a href="/" class="hover:text-gray-600 transition-colors">Home</a>
          <a href="/gallery" class="hover:text-gray-600 transition-colors">Gallery</a>
        </div>
      </div>
    </nav>

    <NuxtPage />
    
    <footer class="bg-gray-100 text-gray-600 py-6">
      <div class="container mx-auto text-center">
        <p class="text-sm">&copy; 2024 VSQO. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

body {
  font-family: 'Inter', sans-serif;
}
</style>