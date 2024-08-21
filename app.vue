<template>
  <div>
    <nav class="bg-white text-gray-800 py-4 shadow-md border-b border-gray-200">
      <div class="container mx-auto flex justify-between items-center px-6">
        <a href="/" class="text-3xl font-semibold">VSQO</a>
        <div class="space-x-4">
          <a href="/" class="nav-link">Home</a>
          <a href="/gallery" class="nav-link">Gallery</a>
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

.nav-link {
  position: relative;
  padding-bottom: 2px;
  transition: color 0.3s ease;
}

.nav-link::before {
  content: '';
  position: absolute;
  width: 0%;
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #4f46e5;
  transition: width 0.3s ease;
}

.nav-link:hover {
  color: #4f46e5;
}

.nav-link:hover::before {
  width: 100%;
}

footer {
  background-color: #f7fafc;
}

footer p {
  color: #4a5568;
}
</style>
