<template>
  <div>
    <header class="bg-gray-800 p-4">
      <nav class="container mx-auto flex justify-between text-white">
        <h1 class="text-2xl font-bold">VSQO</h1>
        <ul class="flex space-x-4">
          <li><NuxtLink to="/">Home</NuxtLink></li>
          <li><NuxtLink to="/gallery">Gallery</NuxtLink></li>
          <li><NuxtLink to="/about">About</NuxtLink></li>
        </ul>
      </nav>
    </header>
    <main class="container mx-auto py-8">
      <NuxtPage />
    </main>
    <footer class="bg-gray-800 text-center text-white py-4">
      © 2024 VSQO. All rights reserved.
    </footer>
  </div>
</template>
