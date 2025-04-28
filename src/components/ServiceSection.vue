<template>
  <section class="services-accordion-section py-16 bg-white">
    <div class="container mx-auto px-4 md:pl-14">
      <h2 class="section-title text-3xl md:text-4xl font-bold text-gray-800 mb-8 pb-4 relative">Our Services</h2>
      
      <div class="accordion-container">
        <!-- Building Services Accordion -->
        <div class="accordion-item mb-4 border border-gray-200 rounded-lg overflow-hidden">
          <button 
            class="accordion-header w-full flex justify-between items-center p-5 bg-white hover:bg-gray-50 transition-colors"
            @click="toggleAccordion(0)"
          >
            <h3 class="text-xl font-semibold">BUILDING SERVICES</h3>
            <div class="accordion-icon">
              <svg 
                xmlns="http://www.w3.org/2000/svg" 
                width="24" 
                height="24" 
                viewBox="0 0 24 24" 
                fill="none" 
                stroke="currentColor" 
                stroke-width="2" 
                stroke-linecap="round" 
                stroke-linejoin="round" 
                :class="{'transform rotate-180': activeIndex === 0}"
                class="transition-transform duration-300"
              >
                <path d="M6 9l6 6 6-6"/>
              </svg>
            </div>
          </button>
          <div 
            class="accordion-content overflow-hidden transition-all duration-300"
            :style="{ maxHeight: activeIndex === 0 ? '1000px' : '0' }"
          >
            <div class="p-5 bg-gray-50 border-t border-gray-200">
              <p class="mb-4 text-gray-700">CMSS provides a 24/7 fast and reliable reactive maintenance service in Greater London and Home Counties.</p>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <ul class="pl-5 list-none">
                  <li v-for="(point, index) in buildingPoints" :key="index" class="flex items-start mb-3">
                    <svg class="h-5 w-5 text-blue-600 mr-2 flex-shrink-0 mt-1" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                    </svg>
                    <span>{{ point }}</span>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>

        <!-- Maintenance Services Accordion -->
        <div class="accordion-item mb-4 border border-gray-200 rounded-lg overflow-hidden">
          <button 
            class="accordion-header w-full flex justify-between items-center p-5 bg-white hover:bg-gray-50 transition-colors"
            @click="toggleAccordion(1)"
          >
            <h3 class="text-xl font-semibold">MAINTENANCE SERVICES</h3>
            <div class="accordion-icon">
              <svg 
                xmlns="http://www.w3.org/2000/svg" 
                width="24" 
                height="24" 
                viewBox="0 0 24 24" 
                fill="none" 
                stroke="currentColor" 
                stroke-width="2" 
                stroke-linecap="round" 
                stroke-linejoin="round" 
                :class="{'transform rotate-180': activeIndex === 1}"
                class="transition-transform duration-300"
              >
                <path d="M6 9l6 6 6-6"/>
              </svg>
            </div>
          </button>
          <div 
            class="accordion-content overflow-hidden transition-all duration-300"
            :style="{ maxHeight: activeIndex === 1 ? '1000px' : '0' }"
          >
            <div class="p-5 bg-gray-50 border-t border-gray-200">
              <p class="mb-4 text-gray-700">CMSS specializes in delivering top-quality maintenance services, ensuring every task is handled with precision and care. Our team is reliable, proactive, and committed to keeping properties in excellent condition.</p>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <ul class="pl-5 list-none">
                  <li v-for="(point, index) in maintenancePoints" :key="index" class="flex items-start mb-3">
                    <svg class="h-5 w-5 text-blue-600 mr-2 flex-shrink-0 mt-1" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                    </svg>
                    <span>{{ point }}</span>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>

        <!-- Mechanical Services Accordion -->
        <div class="accordion-item mb-4 border border-gray-200 rounded-lg overflow-hidden">
          <button 
            class="accordion-header w-full flex justify-between items-center p-5 bg-white hover:bg-gray-50 transition-colors"
            @click="toggleAccordion(2)"
          >
            <h3 class="text-xl font-semibold">MECHANICAL SERVICES</h3>
            <div class="accordion-icon">
              <svg 
                xmlns="http://www.w3.org/2000/svg" 
                width="24" 
                height="24" 
                viewBox="0 0 24 24" 
                fill="none" 
                stroke="currentColor" 
                stroke-width="2" 
                stroke-linecap="round" 
                stroke-linejoin="round" 
                :class="{'transform rotate-180': activeIndex === 2}"
                class="transition-transform duration-300"
              >
                <path d="M6 9l6 6 6-6"/>
              </svg>
            </div>
          </button>
          <div 
            class="accordion-content overflow-hidden transition-all duration-300"
            :style="{ maxHeight: activeIndex === 2 ? '1000px' : '0' }"
          >
            <div class="p-5 bg-gray-50 border-t border-gray-200">
              <p class="mb-4 text-gray-700">CMSS has vast experience in undertaking planned servicing programmes to a wide range of installed equipment, from domestic gas boilers through to complex communal plant services.</p>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <ul class="pl-5 list-none">
                  <li v-for="(point, index) in mechanicalPoints" :key="index" class="flex items-start mb-3">
                    <svg class="h-5 w-5 text-blue-600 mr-2 flex-shrink-0 mt-1" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                    </svg>
                    <span>{{ point }}</span>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>

        <!-- Cleaning Services Accordion -->
        <div class="accordion-item mb-4 border border-gray-200 rounded-lg overflow-hidden">
          <button 
            class="accordion-header w-full flex justify-between items-center p-5 bg-white hover:bg-gray-50 transition-colors"
            @click="toggleAccordion(3)"
          >
            <h3 class="text-xl font-semibold">CLEANING SERVICES</h3>
            <div class="accordion-icon">
              <svg 
                xmlns="http://www.w3.org/2000/svg" 
                width="24" 
                height="24" 
                viewBox="0 0 24 24" 
                fill="none" 
                stroke="currentColor" 
                stroke-width="2" 
                stroke-linecap="round" 
                stroke-linejoin="round" 
                :class="{'transform rotate-180': activeIndex === 3}"
                class="transition-transform duration-300"
              >
                <path d="M6 9l6 6 6-6"/>
              </svg>
            </div>
          </button>
          <div 
            class="accordion-content overflow-hidden transition-all duration-300"
            :style="{ maxHeight: activeIndex === 3 ? '1000px' : '0' }"
          >
            <div class="p-5 bg-gray-50 border-t border-gray-200">
              <p class="mb-4 text-gray-700">CMSS is effective at providing cleaning services and we are very detail-oriented in our work. We are efficient and thorough, and get the job done well and in a timely manner.</p>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <ul class="pl-5 list-none">
                  <li v-for="(point, index) in cleaningPoints.slice(0, Math.ceil(cleaningPoints.length/2))" :key="index" class="flex items-start mb-3">
                    <svg class="h-5 w-5 text-blue-600 mr-2 flex-shrink-0 mt-1" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                    </svg>
                    <span>{{ point }}</span>
                  </li>
                </ul>
                <ul class="pl-5 list-none">
                  <li v-for="(point, index) in cleaningPoints.slice(Math.ceil(cleaningPoints.length/2))" :key="index + Math.ceil(cleaningPoints.length/2)" class="flex items-start mb-3">
                    <svg class="h-5 w-5 text-blue-600 mr-2 flex-shrink-0 mt-1" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                    </svg>
                    <span>{{ point }}</span>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ServicesAccordion',
  data() {
    return {
      activeIndex: null, // Initially no accordion is open
      buildingPoints: [
        "24/7 Maintenance Helpdesk",
        "Reactive Maintenance",
        "Major Refurbishment Works",
        "Minor Works Projects"
      ],
      maintenancePoints: [
        "Drainage",
        "Roofing",
        "Plumbing",
        "Electrics",
        "Painting and Decorating"
      ],
      mechanicalPoints: [
        "Compliance & Planned Maintenance",
        "Water Safety/Legionella",
        "M&E Plant and Equipment",
        "Air Conditioning",
        "Heating",
        "Ventilation"
      ],
      cleaningPoints: [
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
  },
  methods: {
    toggleAccordion(index) {
      // If clicking on the currently open accordion, close it
      if (this.activeIndex === index) {
        this.activeIndex = null;
      } else {
        // Otherwise, open the clicked accordion
        this.activeIndex = index;
      }
    }
  }
}
</script>

<style scoped>
.services-accordion-section {
  background-color: #ffffff;
}

.section-title {
  font-size: 2.25rem;
  font-weight: 600;
  color: #333;
  margin-bottom: 1.5rem;
  position: relative;
  padding-bottom: 1rem;
}

.section-title:after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  height: 4px;
  width: 60px;
  background-color: #4a6cf7;
}

.accordion-item {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  transition: box-shadow 0.3s ease;
}

.accordion-item:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.accordion-header {
  cursor: pointer;
  user-select: none;
}

/* Blue tint for the active accordion header */
.accordion-header:focus, 
.accordion-header:active {
  background-color: #f0f7ff;
  outline: none;
}

/* The transition effect when expanding/collapsing content */
.accordion-content {
  transition: max-height 0.3s ease-in-out;
}

/* Style for the check icons in bullet points */
ul li svg {
  color: #4a6cf7;
}

@media (max-width: 768px) {
  .section-title {
    font-size: 1.75rem;
  }
  
  .accordion-item h3 {
    font-size: 1.1rem;
  }
  
  .accordion-content p {
    font-size: 0.95rem;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 1.5rem;
  }
}
</style>