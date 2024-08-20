<template>
    <div>
      <!-- Main Content -->
      <main class="relative py-16 bg-gray-100 min-h-screen overflow-hidden">
        <h1 class="text-5xl font-bold text-gray-800 mb-12 text-center">VSQO 🍍</h1>
        <div class="relative w-full h-full">
          <canvas id="objectsCanvas" class="absolute top-0 left-0 w-full h-full pointer-events-none"></canvas>
        </div>
      </main>
    </div>
  </template>
  
  <script setup>
  import { onMounted } from 'vue';
  import gsap from 'gsap';
  
  onMounted(() => {
    const canvas = document.getElementById('objectsCanvas');
    const ctx = canvas.getContext('2d');
    const objects = [];
  
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  
    function createObject() {
      const size = Math.random() * 30 + 10;
      objects.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        size,
        speedX: Math.random() * 2 - 1,
        speedY: Math.random() * 2 - 1,
        color: `rgba(${Math.floor(Math.random() * 255)}, ${Math.floor(Math.random() * 255)}, ${Math.floor(Math.random() * 255)}, 0.5)`
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
  
    for (let i = 0; i < 100; i++) {
      createObject();
    }
  
    animate();
  });
  </script>
  