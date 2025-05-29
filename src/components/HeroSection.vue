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
import { heroImages } from '@/assets/images.js'

export default {
  setup() {
    const slides = [
      {
        title: "Expert Property Maintenance Services",
        description: "Capital Maintenance and Support Services Ltd provides comprehensive property maintenance solutions across London and the South East.",
        image: heroImages.heroImage1,
        bulletPoints: [
          "24/7 Emergency Response",
          "Fully Qualified Technicians", 
          "Comprehensive Insurance Coverage",
          "Single Source Service Delivery"
        ]
      },
      {
        title: "Trusted by Property Professionals",
        description: "Serving residential and commercial managing agents, landlords, freeholders, retailers, and hospitality providers since 2020.",
        image: heroImages.heroImage2,
        bulletPoints: [
          "Residential & Commercial Properties",
          "Managing Agent Partnerships",
          "Retail & Hospitality Specialists",
          "Insurance Claim Support"
        ]
      },
      {
        title: "Complete Maintenance Solutions",
        description: "From routine maintenance to emergency repairs, we handle all aspects of your property maintenance needs with our in-house expertise.",
        image: heroImages.heroImage1,
        bulletPoints: [
          "Plumbing & Heating",
          "Electrical Services",
          "General Building Work",
          "Preventive Maintenance Programs"
        ]
      },
      {
        title: "Quality You Can Trust",
        description: "Our commitment to excellence and customer satisfaction sets us apart from competitors in the property maintenance industry.",
        image: heroImages.heroImage2,
        bulletPoints: [
          "Quality Guaranteed Work",
          "Competitive Pricing",
          "Fast Response Times",
          "Professional Service Standards"
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