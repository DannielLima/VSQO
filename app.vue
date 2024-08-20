<template>
  <div>
    <nav class="bg-white text-gray-800 py-4 shadow-md border-b border-gray-200">
      <div class="container mx-auto flex justify-between items-center px-6">
        <a href="/" class="text-3xl font-semibold" id="navBrand">VSQO</a>
        <div class="space-x-4" id="navLinks">
          <a href="/" class="hover:text-gray-600 transition-colors" id="navHome">Home</a>
          <a href="/gallery" class="hover:text-gray-600 transition-colors" id="navGallery">Gallery</a>
        </div>
      </div>
    </nav>

    <NuxtPage />
    
    <footer class="bg-gray-100 text-gray-600 py-6" id="footer">
      <div class="container mx-auto text-center">
        <p class="text-sm">&copy; 2024 VSQO. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { onMounted } from 'vue';
import gsap from 'gsap';

onMounted(() => {
  gsap.fromTo(
    '#navBrand',
    { opacity: 0, x: -50 },
    { opacity: 1, x: 0, duration: 1, ease: 'power3.out' }
  );
  gsap.fromTo(
    '#navLinks a',
    { opacity: 0, y: -20 },
    { opacity: 1, y: 0, duration: 1, stagger: 0.2, ease: 'power3.out' }
  );

  gsap.fromTo(
    '#footer',
    { opacity: 0, y: 20 },
    { opacity: 1, y: 0, duration: 1, ease: 'power3.out' }
  );
});
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

body {
  font-family: 'Inter', sans-serif;
}

nav {
  display: flex;
  justify-content: center;
}

#navBrand {
  font-size: 1.5rem;
}

#navLinks {
  display: flex;
  gap: 1rem;
}

footer {
  display: flex;
  justify-content: center;
}

@media (max-width: 768px) {
  nav {
    flex-direction: column;
    align-items: center;
  }

  #navLinks {
    flex-direction: column;
    gap: 0.5rem;
  }

  footer {
    padding: 2rem 0;
  }
}
</style>