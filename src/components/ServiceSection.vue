<template>
  <section class="service-section">
    <div class="container">
      <div class="service-grid">
        <div v-for="service in visibleServices" :key="service.id" class="service-card">
          <router-link :to="service.link" class="service-link">
            <div class="image-container">
              <img :src="service.image" :alt="service.title" class="service-image" />
            </div>
          </router-link>
          <div class="service-title">
            <h3>{{ service.title }}</h3>
            <div class="arrow-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <circle cx="12" cy="12" r="10" />
                <path d="M12 16l4-4-4-4" />
                <path d="M8 12h8" />
              </svg>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Show more/less button -->
      <div class="view-more-container" id="view-more-btn-container">
        <button @click="toggleViewMore" class="view-more-btn" id="view-more-button">
          <span>{{ showAll ? 'Show Less Services' : 'View All Services' }}</span>
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="btn-icon" :class="{'rotate-icon': showAll}">
            <path d="M6 9l6 6 6-6"/>
          </svg>
        </button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ServiceSection',
  data() {
    return {
      showAll: false,
      itemsPerRow: 3,
      rowsToShow: 1,
      buttonVisible: true, // Explicitly track button visibility
      services: [
        {
          id: 1,
          title: 'Core Project Services',
          image: '/images/core-project-services.jpg',
          link: '/services/core-project'
        },
        {
          id: 2,
          title: 'Drying Services',
          image: '/images/drying-services.jpg',
          link: '/services/drying'
        },
        {
          id: 3,
          title: 'Maintenance Services',
          image: '/images/maintenance-services.jpg',
          link: '/services/maintenance'
        },
        {
          id: 4,
          title: 'Building Services',
          image: '/images/building-services.jpg',
          link: '/services/building'
        },
        {
          id: 5,
          title: 'Mechanical Services',
          image: '/images/mechanical-services.jpg',
          link: '/services/mechanical'
        },
        {
          id: 6,
          title: 'Cleaning Services',
          image: '/images/cleaning-services.jpg',
          link: '/services/cleaning'
        }
      ]
    }
  },
  computed: {
    visibleServices() {
      return this.showAll 
        ? this.services 
        : this.services.slice(0, this.itemsPerRow * this.rowsToShow);
    },
    hasMoreServices() {
      return this.services.length > this.itemsPerRow * this.rowsToShow;
    }
  },
  methods: {
    toggleViewMore() {
      this.showAll = !this.showAll;
      console.log('Button clicked, showAll:', this.showAll);
    },
    checkButtonVisibility() {
      // Force the button to be visible
      setTimeout(() => {
        const button = document.getElementById('view-more-button');
        const container = document.getElementById('view-more-btn-container');
        
        if (button && container) {
          button.style.display = 'flex';
          container.style.display = 'flex';
          this.buttonVisible = true;
          console.log('Button visibility enforced');
        }
      }, 100);
    }
  },
  // Enhanced mounted hook to check button visibility
  mounted() {
    console.log('Component mounted');
    console.log('Initial state - showAll:', this.showAll);
    console.log('Services count:', this.services.length);
    console.log('Visible services count:', this.visibleServices.length);
    
    // Check and enforce button visibility
    this.checkButtonVisibility();
    
    // Recheck button visibility after a short delay to ensure DOM is fully rendered
    setTimeout(this.checkButtonVisibility, 500);
  },
  // Added updated lifecycle hook to ensure button visibility after updates
  updated() {
    this.checkButtonVisibility();
  }
}
</script>

<style scoped>
.service-section {
  padding: 4rem 0;
  background-color: #ffffff;
  position: relative; /* Establish stacking context */
  overflow: visible; /* Ensure content isn't cut off */
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.service-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 2.5rem;
  margin-bottom: 3rem; /* Add explicit margin to ensure space for button */
}

.service-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  transition: transform 0.3s ease;
}

.service-card:hover {
  transform: translateY(-5px);
}

.service-link {
  display: block;
  text-decoration: none;
  color: inherit;
}

.image-container {
  width: 100%;
  height: 160px;
  overflow: hidden;
  border-radius: 0.5rem;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  aspect-ratio: 16/9;
}

.service-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.service-card:hover .service-image {
  transform: scale(1.05);
}

.service-title {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem 0.5rem;
  margin-top: 1rem;
  text-align: center;
}

.service-title h3 {
  margin: 0;
  font-size: 1.15rem;
  color: #333333;
  font-weight: 500;
}

.arrow-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  color: #4a6cf7;
  margin-left: 0.5rem;
}

/* Fixed view-more container to ensure button visibility */
.view-more-container {
  display: flex;
  justify-content: center;
  margin-top: 3rem;
  margin-bottom: 2rem;
  min-height: 50px;
  position: relative;
  z-index: 10;
  visibility: visible;
  width: 100%;
}

.view-more-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0.75rem 1.5rem;
  background-color: #4a6cf7;
  color: white;
  border: none;
  border-radius: 0.5rem;
  font-size: 1.1rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 12px rgba(74, 108, 247, 0.25);
  position: relative;
  overflow: hidden;
  min-width: 220px;
  height: auto;
  opacity: 1;
  line-height: 1.5;
  margin: 0 auto; /* Center the button horizontally */
}

.view-more-btn:before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 0;
  background-color: rgba(255, 255, 255, 0.1);
  transition: width 0.3s ease;
  z-index: 1;
}

.view-more-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 16px rgba(74, 108, 247, 0.3);
}

.view-more-btn:hover:before {
  width: 100%;
}

.view-more-btn:active {
  transform: translateY(-1px);
}

.view-more-btn span {
  position: relative;
  z-index: 2;
  color: white; /* Ensure text is white and visible */
}

.btn-icon {
  margin-left: 0.75rem;
  transition: transform 0.3s ease;
  position: relative;
  z-index: 2;
}

.rotate-icon {
  transform: rotate(180deg);
}

/* Media queries for responsiveness */
@media (min-width: 640px) {
  .service-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }
}

@media (min-width: 1024px) {
  .service-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }
  
  .service-title h3 {
    font-size: 1.25rem;
  }
}

/* For very small screens */
@media (max-width: 400px) {
  .image-container {
    height: 180px;
  }
  
  .service-title {
    padding: 1rem;
  }
  
  .service-title h3 {
    font-size: 1.1rem;
  }
  
  .view-more-btn {
    padding: 0.75rem 1.25rem;
    font-size: 1rem;
  }
}
</style>