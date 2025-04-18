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

export default {
  setup() {
    const slides = [
      {
        title: "BUILDING SERVICES",
        description: "CMSS provides a 24/7 fast and reliable reactive maintenance service in Greater London and Home Counties.",
        image: "https://source.unsplash.com/random/1920x1080/?construction,building",
        bulletPoints: [
          "24/7 Maintenance Helpdesk",
          "Reactive Maintenance",
          "Major Refurbishment Works",
          "Minor Works Projects"
        ]
      },
      {
        title: "MAINTENANCE SERVICES",
        description: "CMSS specializes in delivering top-quality maintenance services, ensuring every task is handled with precision and care. Our team is reliable, proactive, and committed to keeping properties in excellent condition.",
        image: "https://source.unsplash.com/random/1920x1080/?maintenance,repair",
        bulletPoints: [
          "Drainage",
          "Roofing",
          "Plumbing",
          "Electrics",
          "Painting and Decorating"
        ]
      },
      {
        title: "MECHANICAL SERVICES",
        description: "CMSS has vast experience in undertaking planned servicing programmes to a wide range of installed equipment, from domestic gas boilers through to complex communal plant services.",
        image: "https://source.unsplash.com/random/1920x1080/?mechanical,engineering",
        bulletPoints: [
          "Compliance & Planned Maintenance",
          "Water Safety/Legionella",
          "M&E Plant and Equipment",
          "Air Conditioning",
          "Heating",
          "Ventilation"
        ]
      },
      {
        title: "CLEANING SERVICES",
        description: "CMSS is effective at providing cleaning services and we are very detail-oriented in our work. We are efficient and thorough, and get the job done well and in a timely manner.",
        image: "https://source.unsplash.com/random/1920x1080/?cleaning,service",
        bulletPoints: [
          "Office Cleaning",
          "Window Cleaning",
          "Floor Cleaning",
          "Washroom Services",
          "Waste Management Services",
          "Pressure Washing",
          "Domestic Cleaning",
          "End of Tenancy Cleaning",
          "Carpet Cleaning",
          "Commercial Cleaning"
        ]
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