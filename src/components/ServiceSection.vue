<template>
  <section class="service-section">
    <div class="container">
      <div class="service-grid">
        <div v-for="property in visibleProperties" :key="property.id" class="service-card">
          <router-link :to="property.link" class="service-link">
            <div class="image-container">
              <img :src="property.image" :alt="property.title" class="service-image" />
            </div>
          </router-link>
          <div class="service-title">
            <h3>{{ property.title }}</h3>
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
      
      <!-- Fixed button container -->
      <div class="view-more-container" id="view-more-btn-container">
        <button @click="toggleViewMore" class="view-more-btn" id="view-more-button">
          <span>{{ showAll ? 'Show Less Properties' : 'See Who We Have Helped' }}</span>
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
  name: 'PropertySection',
  data() {
    return {
      showAll: false,
      itemsPerRow: 4,
      rowsToShow: 1,
      buttonVisible: true, // Explicitly track button visibility
      properties: [
        {
          id: 1,
          title: 'SUNLIGHT APARTMENTS',
          image: '/images/sunlight-apartments.jpg',
          link: '/properties/sunlight-apartments'
        },
        {
          id: 2,
          title: 'BERNARD MYERS HOUSE',
          image: '/images/bernard-myers-house.jpg',
          link: '/properties/bernard-myers-house'
        },
        {
          id: 3,
          title: 'VAUXHALL SKY GARDENS',
          image: '/images/vauxhall-sky-gardens.jpg',
          link: '/properties/vauxhall-sky-gardens'
        },
        {
          id: 4,
          title: 'HOOLA APARTMENTS LONDON',
          image: '/images/hoola-apartments.jpg',
          link: '/properties/hoola-apartments'
        },
        {
          id: 5,
          title: 'BRONZE APARTMENTS WANDSWORTH',
          image: '/images/bronze-apartments.jpg',
          link: '/properties/bronze-apartments'
        },
        {
          id: 6,
          title: 'CAMBERWELL ON THE GREEN',
          image: '/images/camberwell-on-the-green.jpg',
          link: '/properties/camberwell-on-the-green'
        },
        {
          id: 7,
          title: 'VIZON 7 HOLLOWAY',
          image: '/images/vizon-7-holloway.jpg',
          link: '/properties/vizon-7-holloway'
        },
        {
          id: 8,
          title: 'CITY PENNINSULA GREENWICH',
          image: '/images/city-penninsula.jpg',
          link: '/properties/city-penninsula'
        },
        {
          id: 9,
          title: 'ERNEST WEBSDALE BARKING RIVERSIDE',
          image: '/images/ernest-websdale.jpg',
          link: '/properties/ernest-websdale'
        },
        {
          id: 10,
          title: 'OVAL QUARTER',
          image: '/images/oval-quarter.jpg',
          link: '/properties/oval-quarter'
        },
        {
          id: 11,
          title: 'BLUEBIRD HOUSE BARKING RIVERSIDE',
          image: '/images/bluebird-house.jpg',
          link: '/properties/bluebird-house'
        },
        {
          id: 12,
          title: 'TOTTENHAM HALE',
          image: '/images/tottenham-hale.jpg',
          link: '/properties/tottenham-hale'
        }
      ]
    }
  },
  computed: {
    visibleProperties() {
      return this.showAll 
        ? this.properties 
        : this.properties.slice(0, this.itemsPerRow * this.rowsToShow);
    },
    hasMoreProperties() {
      return this.properties.length > this.itemsPerRow * this.rowsToShow;
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
    console.log('Properties count:', this.properties.length);
    console.log('Visible properties count:', this.visibleProperties.length);
    
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

@media (min-width: 1280px) {
  .service-grid {
    grid-template-columns: repeat(4, 1fr);
    gap: 1.5rem;
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