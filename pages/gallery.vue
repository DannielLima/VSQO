<template>
    <div>
      <!-- Gallery -->
      <main class="py-16 bg-gray-100 min-h-screen flex items-center justify-center">
        <div class="text-center">
          <h1 id="galleryTitle" class="text-4xl font-bold text-gray-800 mb-12 inline-block">
            Gallery
          </h1>
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
        </div>
      </main>
    </div>
  </template>
  
  <script setup>
  import { onMounted, ref, nextTick } from 'vue';
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
  
  onMounted(async () => {
    await nextTick(); // Garante que o DOM esteja pronto
  
    // Animação GSAP para o título "Gallery"
    const titleElement = document.getElementById('galleryTitle');
    titleElement.innerHTML = titleElement.innerText.split('').map(letter => `<span>${letter}</span>`).join('');
  
    gsap.fromTo(
      '#galleryTitle span',
      { scale: 1, opacity: 0 },
      { scale: 1.2, opacity: 1, duration: 1.5, ease: 'elastic.out(1, 0.3)', stagger: 0.1 }
    );
  
    // Animação GSAP para os itens da galeria
    gsap.fromTo(
      galleryItems.value,
      { opacity: 0, y: 20 },
      { opacity: 1, y: 0, stagger: 0.1, duration: 1 }
    );
  });
  </script>
  
  <style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');
  
  body {
    font-family: 'Inter', sans-serif;
  }
  
  /* Efeito 3D para o título */
  #galleryTitle {
    position: relative;
    display: inline-flex;
    flex-wrap: wrap;
    justify-content: center;
    perspective: 1000px; /* Adiciona profundidade ao efeito 3D */
  }
  
  #galleryTitle span {
    display: inline-block;
    transition: transform 0.3s ease, text-shadow 0.3s ease;
    transform-style: preserve-3d; /* Habilita o efeito 3D */
  }
  
  #galleryTitle span:hover {
    transform: rotateX(15deg) rotateY(15deg) scale(1.3);
    text-shadow: 0 4px 6px rgba(0, 0, 0, 0.3), 0 1px 3px rgba(0, 0, 0, 0.1);
  }
  
  /* Centraliza o título e o conteúdo da galeria */
  main {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .grid {
    margin-top: 2rem; /* Espaçamento adicional abaixo do título */
  }
  
  /* Animação de fade-in para os itens da galeria */
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  
  .gallery-item {
    animation: fadeIn 1s ease-in;
  }
  </style>
  