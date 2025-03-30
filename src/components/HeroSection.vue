<template>
    <!-- Hero section with background and slide navigation -->
    <section class="h-screen relative flex items-center overflow-hidden bg-[#4b84b4]">
      <!-- Slider images -->
      <div class="absolute inset-0 bg-cover bg-center z-0 transition-opacity duration-500"
           :style="{ 
              backgroundImage: `url(${slides[currentSlide].image})`,
              opacity: fadeState ? 1 : 0
           }">
      </div>
      
      <!-- Overlay -->
      <div class="absolute inset-0 bg-black opacity-40 z-10"></div>
      
      <!-- Left arrow navigation -->
      <div class="absolute left-4 top-1/2 z-30 transform -translate-y-1/2">
        <button @click="prevSlide" class="w-10 h-10 flex items-center justify-center text-white hover:text-gray-300">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
          </svg>
        </button>
      </div>
      
      <!-- Right arrow navigation -->
      <div class="absolute right-4 top-1/2 z-30 transform -translate-y-1/2">
        <button @click="nextSlide" class="w-10 h-10 flex items-center justify-center text-white hover:text-gray-300">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
        </button>
      </div>
      
      <!-- Content -->
      <div class="container mx-auto px-6 relative z-20 text-white">
        <h1 class="text-6xl md:text-8xl font-bold mb-4">
          {{ slides[currentSlide].title }}
        </h1>
        <p class="text-xl md:text-2xl max-w-3xl">
          {{ slides[currentSlide].description }}
        </p>
      </div>
    </section>
  </template>
  
  <script>
  import { ref, onMounted, onBeforeUnmount } from 'vue'
  import { gsap } from 'gsap'
  
  export default {
    setup() {
      const slides = [
        {
          title: "Maintenance",
          description: "Professional property maintenance services for residential and commercial properties",
          image: "https://source.unsplash.com/random/1920x1080/?construction"
        },
        {
          title: "Renovation",
          description: "Transform your space with our expert renovation services",
          image: "https://source.unsplash.com/random/1920x1080/?renovation"
        },
        {
          title: "Solutions",
          description: "Innovative solutions for all your property needs",
          image: "https://source.unsplash.com/random/1920x1080/?architecture"
        }
      ]
      
      const currentSlide = ref(0)
      const fadeState = ref(true)
      let slideInterval = null
      
      const nextSlide = () => {
        fadeState.value = false
        
        setTimeout(() => {
          currentSlide.value = (currentSlide.value + 1) % slides.length
          fadeState.value = true
        }, 500)
      }
      
      const prevSlide = () => {
        fadeState.value = false
        
        setTimeout(() => {
          currentSlide.value = (currentSlide.value - 1 + slides.length) % slides.length
          fadeState.value = true
        }, 500)
      }
      
      onMounted(() => {
        // Set up auto-sliding
        slideInterval = setInterval(nextSlide, 7000)
        
        // Animate heading text
        gsap.from('h1', {
          opacity: 0,
          y: 50,
          duration: 1,
          delay: 0.3
        })
        
        gsap.from('p', {
          opacity: 0,
          y: 30,
          duration: 1,
          delay: 0.6
        })
      })
      
      onBeforeUnmount(() => {
        if (slideInterval) clearInterval(slideInterval)
      })
      
      return {
        slides,
        currentSlide,
        fadeState,
        nextSlide,
        prevSlide
      }
    }
  }
  </script>