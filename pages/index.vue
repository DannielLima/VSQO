<template>
  <div>
    <main class="relative py-16 bg-gray-100 min-h-screen overflow-hidden">
      <div class="text-center relative z-10">
        <h1 id="animatedText" class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-bold text-gray-800 mb-12">
          BELIEVE IN YOURSELF
        </h1>
        <p class="text-md text-gray-500 mb-8">
          Discover your potential and embrace new opportunities.
        </p>
        <a href="/gallery" class="gallery-button px-8 py-4 bg-indigo-600 text-white text-lg font-semibold rounded-lg shadow-md hover:bg-indigo-500 hover:shadow-lg transition-all duration-300 focus:outline-none focus:ring-2 focus:ring-indigo-300">
          Gallery
        </a>
      </div>
      <div class="relative w-full h-full">
        <canvas id="objectsCanvas" class="absolute top-0 left-0 w-full h-full pointer-events-none"></canvas>
      </div>
    </main>
  </div>
</template>

<script setup>
import { onMounted, nextTick } from 'vue';

onMounted(async () => {
  await nextTick();

  const canvas = document.getElementById('objectsCanvas');
  const ctx = canvas.getContext('2d');
  const objects = [];
  const numberOfObjects = 150;

  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  function createObject() {
    const size = Math.random() * 5 + 5;
    objects.push({
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height,
      size,
      speedX: Math.random() * 2 - 1,
      speedY: Math.random() * 2 - 1,
      color: `rgba(${Math.floor(Math.random() * 255)}, ${Math.floor(Math.random() * 255)}, ${Math.floor(Math.random() * 255)}, 0.6)`
    });
  }

  function drawObjects() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    objects.forEach(obj => {
      ctx.beginPath();
      ctx.arc(obj.x, obj.y, obj.size, 0, Math.PI * 2);
      ctx.fillStyle = obj.color;
      ctx.fill();
    });
  }

  function updateObjects() {
    objects.forEach(obj => {
      obj.x += obj.speedX;
      obj.y += obj.speedY;

      if (obj.x > canvas.width || obj.x < 0) obj.speedX *= -1;
      if (obj.y > canvas.height || obj.y < 0) obj.speedY *= -1;
    });
  }

  function animate() {
    drawObjects();
    updateObjects();
    requestAnimationFrame(animate);
  }

  for (let i = 0; i < numberOfObjects; i++) {
    createObject();
  }

  animate();
});
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

body {
  font-family: 'Inter', sans-serif;
}

main {
  position: relative;
}

@media (max-width: 640px) {
  #animatedText {
    font-size: 2xl;
  }
}

@media (min-width: 640px) and (max-width: 768px) {
  #animatedText {
    font-size: 3xl;
  }
}

@media (min-width: 768px) and (max-width: 1024px) {
  #animatedText {
    font-size: 4xl;
  }
}

@media (min-width: 1024px) {
  #animatedText {
    font-size: 5xl;
  }
}

.gallery-button {
  background-color: #4f46e5;
  transition: background-color 0.3s ease, box-shadow 0.3s ease;
}

.gallery-button:hover {
  background-color: #4338ca;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.gallery-button:focus {
  box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.5);
}
</style>