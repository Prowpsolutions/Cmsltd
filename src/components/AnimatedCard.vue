<template>
    <div class="flex justify-center items-center min-h-screen bg-gray-100">
      <div 
        ref="card" 
        class="bg-white rounded-lg shadow-lg p-8 max-w-md transform transition-all duration-300 hover:shadow-xl"
        @mouseenter="animateIn"
        @mouseleave="animateOut"
      >
        <h2 class="text-2xl font-bold text-gray-800 mb-4">CMS Ltd</h2>
        <p class="text-gray-600 mb-6">Welcome to our innovative content management solution.</p>
        <button class="bg-blue-500 hover:bg-blue-600 text-white font-semibold py-2 px-4 rounded">
          Learn More
        </button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  import { gsap } from 'gsap';
  
  const card = ref(null);
  
  onMounted(() => {
    // Initial animation when component mounts
    gsap.from(card.value, {
      y: 50,
      opacity: 0,
      duration: 1,
      ease: 'power3.out'
    });
  });
  
  const animateIn = () => {
    gsap.to(card.value, {
      scale: 1.05,
      duration: 0.3,
      ease: 'power1.out'
    });
  };
  
  const animateOut = () => {
    gsap.to(card.value, {
      scale: 1,
      duration: 0.3,
      ease: 'power1.in'
    });
  };
  </script>