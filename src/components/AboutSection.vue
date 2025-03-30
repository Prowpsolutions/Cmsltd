<template>
    <section class="py-16 bg-white">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold mb-8">CMS Ltd</h2>
        <p class="text-lg mb-6 max-w-3xl">
          Welcome to our innovative content management solution.
          We provide cutting-edge digital tools designed to streamline
          your workflow and enhance your online presence.
        </p>
        <button class="px-6 py-2 border border-black hover:bg-gray-100 transition-all">
          Learn More
        </button>
      </div>
    </section>
  </template>
  
  <script>
  import { onMounted } from 'vue'
  import { gsap } from 'gsap'
  import { ScrollTrigger } from 'gsap/ScrollTrigger'
  
  export default {
    setup() {
      onMounted(() => {
        gsap.registerPlugin(ScrollTrigger)
        
        // Create animation that triggers when scrolled into view
        gsap.from('.py-16 h2, .py-16 p, .py-16 button', {
          opacity: 0,
          y: 30,
          stagger: 0.2,
          duration: 0.8,
          scrollTrigger: {
            trigger: '.py-16',
            start: 'top 80%',
            end: 'bottom 20%',
            toggleActions: 'play none none none'
          }
        })
      })
    }
  }
  </script>