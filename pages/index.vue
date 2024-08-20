<template>
    <div>
      <!-- Main Content -->
      <main class="relative py-16 bg-gray-100 min-h-screen overflow-hidden">
        <div class="text-center relative z-10">
          <h1 id="animatedText" class="text-5xl font-bold text-gray-800 mb-12 flex flex-wrap justify-center">
            <!-- Texto renderizado aqui -->
          </h1>
        </div>
        <div class="relative w-full h-full">
          <canvas id="objectsCanvas" class="absolute top-0 left-0 w-full h-full pointer-events-none"></canvas>
        </div>
      </main>
    </div>
  </template>
  
  <script setup>
  import { onMounted, ref, nextTick } from 'vue';
  import gsap from 'gsap';
  
  // Separar o texto em letras
  const textContent = 'VSQO';
  
  onMounted(async () => {
    await nextTick(); // Garante que o DOM esteja pronto
  
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
  
    // Renderiza o texto separando as letras
    const textElement = document.getElementById('animatedText');
    textElement.innerHTML = textContent.split('').map(letter => `<span>${letter}</span>`).join('');
  
    // GSAP animação após renderização
    gsap.fromTo(
      '#animatedText span',
      { scale: 1, opacity: 0 },
      { scale: 1.2, opacity: 1, duration: 1.5, ease: 'elastic.out(1, 0.3)', stagger: 0.1 }
    );
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
  
  #animatedText {
    position: relative;
    display: inline-flex;
    flex-wrap: wrap;
    justify-content: center;
    perspective: 1000px; /* Adiciona profundidade ao efeito 3D */
  }
  
  #animatedText span {
    display: inline-block;
    transition: transform 0.3s ease, text-shadow 0.3s ease;
    transform-style: preserve-3d; /* Habilita o efeito 3D */
  }
  
  #animatedText span:hover {
    transform: rotateX(15deg) rotateY(15deg) scale(1.3);
    text-shadow: 0 4px 6px rgba(0, 0, 0, 0.3), 0 1px 3px rgba(0, 0, 0, 0.1);
  }
  </style>
  