<template>
    <header class="fixed w-full z-50">
      <!-- Desktop navigation -->
      <nav class="container mx-auto px-6 py-4 flex justify-between items-center text-white">
        <!-- Logo -->
        <div class="text-3xl font-bold tracking-wider">
          <span class="text-white">CMSLTD</span>
        </div>
        
        <!-- Navigation and phone on right side -->
        <div class="hidden md:flex items-center">
          <!-- Navigation links - desktop -->
          <div class="flex items-center space-x-8 mr-8">
            <a href="#" class="hover:text-gray-300 transition-colors">Home</a>
            <a href="#" class="hover:text-gray-300 transition-colors">About</a>
            <a href="#" class="hover:text-gray-300 transition-colors">Services</a>
            <a href="#" class="hover:text-gray-300 transition-colors">Projects</a>
            <a href="#" class="hover:text-gray-300 transition-colors">Contact</a>
          </div>
          
          <!-- Phone number -->
          <div class="font-bold text-lg">01689 861 007</div>
        </div>
        
        <!-- Mobile menu button -->
        <button class="md:hidden text-white" @click="toggleMobileMenu">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path v-if="!mobileMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </nav>
      
      <!-- Mobile navigation -->
      <div v-if="mobileMenuOpen" class="md:hidden bg-black bg-opacity-90 text-white">
        <div class="container mx-auto px-6 py-4 space-y-3">
          <a href="#" class="block hover:text-gray-300 transition-colors">Home</a>
          <a href="#" class="block hover:text-gray-300 transition-colors">About</a>
          <a href="#" class="block hover:text-gray-300 transition-colors">Services</a>
          <a href="#" class="block hover:text-gray-300 transition-colors">Projects</a>
          <a href="#" class="block hover:text-gray-300 transition-colors">Contact</a>
          <div class="pt-2 font-bold">01689 861 007</div>
        </div>
      </div>
    </header>
  </template>
  
  <script>
  export default {
    data() {
      return {
        mobileMenuOpen: false
      }
    },
    methods: {
      toggleMobileMenu() {
        this.mobileMenuOpen = !this.mobileMenuOpen
      }
    }
  }
  </script>