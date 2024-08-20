<template>
    <section class="flex items-center justify-center h-screen bg-gradient-to-r from-blue-500 to-purple-500">
      <div class="text-center text-white p-8 rounded-lg bg-opacity-90 backdrop-filter backdrop-blur-lg">
        <h1 class="text-5xl font-extrabold mb-6 animate-fade-in-down">Welcome to VSQO</h1>
        <p class="text-lg mb-8 animate-fade-in-up">Capture and share your best shots.</p>
        <NuxtLink to="/gallery" class="text-lg font-semibold bg-white text-blue-600 px-6 py-3 rounded-full hover:bg-blue-100 transition-colors">Explore Gallery</NuxtLink>
      </div>
    </section>
  </template>
  
  <style>
  @keyframes fade-in-down {
    0% {
      opacity: 0;
      transform: translateY(-20px);
    }
    100% {
      opacity: 1;
      transform: translateY(0);
    }
  }
  
  @keyframes fade-in-up {
    0% {
      opacity: 0;
      transform: translateY(20px);
    }
    100% {
      opacity: 1;
      transform: translateY(0);
    }
  }
  
  .animate-fade-in-down {
    animation: fade-in-down 1s ease-out forwards;
  }
  
  .animate-fade-in-up {
    animation: fade-in-up 1s ease-out forwards;
  }
  </style>
  