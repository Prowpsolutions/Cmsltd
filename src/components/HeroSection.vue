<template>
  <!-- Hero section with background and slide navigation -->
  <section class="h-screen relative flex items-center overflow-hidden bg-[#000000]">
    <!-- Slider images -->
    <div class="absolute inset-0 bg-cover bg-center z-0 transition-opacity duration-500"
         :style="{ 
            backgroundImage: `url(${slides[currentSlide].image})`,
            opacity: fadeState ? 1 : 0
         }">
    </div>
    
    <!-- Overlay -->
    <div class="absolute inset-0 bg-black opacity-40 z-10"></div>
    
    <!-- Content -->
    <div class="container mx-auto px-6 relative z-20 text-white">
      <h1 class="text-3xl md:text-5xl font-bold mb-4">
        {{ slides[currentSlide].title }}
      </h1>
      <p class="text-base md:text-lg max-w-3xl mb-6">
        {{ slides[currentSlide].description }}
      </p>
      <ul v-if="slides[currentSlide].bulletPoints" class="text-sm md:text-base max-w-3xl mb-8 grid grid-cols-1 md:grid-cols-2 gap-2">
        <li v-for="(point, index) in slides[currentSlide].bulletPoints" :key="index" class="flex items-start">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 mr-2 text-blue-300 flex-shrink-0 mt-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
          </svg>
          <span>{{ point }}</span>
        </li>
      </ul>
      <button class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 px-6 rounded-lg transition duration-300 inline-flex items-center">
        Read More
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
        </svg>
      </button>
    </div>
  </section>
</template>

<script>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { gsap } from 'gsap'
// Import your images directly - this is the correct way in Vue/Vite
import heroImage1 from '@/assets/hero-image-1.png'
import heroImage2 from '@/assets/hero-image-2.png'

export default {
  setup() {
    const slides = [
      {
        title: "",
        description: "",
        image: heroImage1,
      },
      {
        title: "",
        description: "",
        image: heroImage2,
      },
      {
        title: "",
        description: "",
        image: heroImage1,
      },
      {
        title: "",
        description: "",
        image: heroImage2,
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
      slideInterval = setInterval(nextSlide, 8000)
      
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

      gsap.from('ul', {
        opacity: 0,
        y: 30,
        duration: 1,
        delay: 0.9
      })

      gsap.from('button', {
        opacity: 0,
        y: 30,
        duration: 1,
        delay: 1.2
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