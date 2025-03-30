<template>
    <div class="fixed bottom-8 left-1/2 transform -translate-x-1/2 z-40">
      <div class="h-10 w-10 rounded-full bg-black flex items-center justify-center cursor-pointer" @click="scrollDown">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
        </svg>
      </div>
    </div>
  </template>
  
  <script>
  import { onMounted } from 'vue'
  import { gsap } from 'gsap'
  
  export default {
    setup() {
      const scrollDown = () => {
        window.scrollTo({
          top: window.innerHeight,
          behavior: 'smooth'
        })
      }
      
      onMounted(() => {
        // Animate down arrow
        gsap.to('.h-10.w-10', {
          y: 10,
          repeat: -1,
          yoyo: true,
          duration: 1.5,
          ease: 'power1.inOut'
        })
      })
      
      return {
        scrollDown
      }
    }
  }
  </script>