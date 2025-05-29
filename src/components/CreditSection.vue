<template>
  <section class="portfolio-section">
    <div class="container">
      <h2 class="section-title">Our Projects</h2>
      <p class="section-description">Explore our diverse range of successful projects across London and the South East.</p>
      
      <!-- Bento Box Grid -->
      <div class="bento-grid">
        <!-- Featured Project (Large) -->
        <div class="bento-item large" @click="showPortfolioModal = true; goToSlide(0)">
          <div class="bento-image" :style="{ backgroundImage: `url(${projects[0].image})` }">
            <div class="bento-overlay">
              <h3>{{ projects[0].name }}</h3>
            </div>
          </div>
        </div>
        
        <!-- Medium Projects -->
        <div class="bento-item medium" @click="showPortfolioModal = true; goToSlide(1)">
          <div class="bento-image" :style="{ backgroundImage: `url(${projects[1].image})` }">
            <div class="bento-overlay">
              <h3>{{ projects[1].name }}</h3>
            </div>
          </div>
        </div>
        
        <div class="bento-item medium" @click="showPortfolioModal = true; goToSlide(2)">
          <div class="bento-image" :style="{ backgroundImage: `url(${projects[2].image})` }">
            <div class="bento-overlay">
              <h3>{{ projects[2].name }}</h3>
            </div>
          </div>
        </div>
        
        <!-- Small Projects -->
        <div class="bento-item small" @click="showPortfolioModal = true; goToSlide(3)">
          <div class="bento-image" :style="{ backgroundImage: `url(${projects[3].image})` }">
            <div class="bento-overlay">
              <h3>{{ projects[3].name }}</h3>
            </div>
          </div>
        </div>
        
        <div class="bento-item small" @click="showPortfolioModal = true; goToSlide(4)">
          <div class="bento-image" :style="{ backgroundImage: `url(${projects[4].image})` }">
            <div class="bento-overlay">
              <h3>{{ projects[4].name }}</h3>
            </div>
          </div>
        </div>
        
        <div class="bento-item small" @click="showPortfolioModal = true; goToSlide(5)">
          <div class="bento-image" :style="{ backgroundImage: `url(${projects[5].image})` }">
            <div class="bento-overlay">
              <h3>{{ projects[5].name }}</h3>
            </div>
          </div>
        </div>
      </div>
      
      <!-- View Full Portfolio Button -->
      <div class="cta-container">
        <a @click.prevent="showPortfolioModal = true" href="#portfolio" class="cta-button">VIEW FULL PORTFOLIO</a>
      </div>
    </div>
    
    <!-- Portfolio Modal with Carousel -->
    <transition name="fade">
      <div v-if="showPortfolioModal" class="modal-overlay" @click.self="showPortfolioModal = false">
        <div class="portfolio-modal">
          <div class="modal-header">
            <h3>Our Portfolio</h3>
            <button @click="showPortfolioModal = false" class="close-btn">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="6" x2="6" y2="18"></line>
                <line x1="6" y1="6" x2="18" y2="18"></line>
              </svg>
            </button>
          </div>
          
          <div class="carousel-container">
            <div class="carousel-slides" ref="slides" :style="{ transform: `translateX(-${currentSlide * 100}%)` }">
              <div v-for="(project, index) in projects" :key="index" class="carousel-slide">
                <div class="project-image" :style="{ backgroundImage: `url(${project.image})` }">
                  <!-- Project name appears only on the active slide -->
                  <div class="project-overlay" :class="{ 'active-overlay': currentSlide === index }">
                    <h3>{{ project.name }}</h3>
                  </div>
                </div>
              </div>
            </div>
            
            <!-- Carousel Navigation -->
            <button class="carousel-nav prev" @click="prevSlide">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <polyline points="15 18 9 12 15 6"></polyline>
              </svg>
            </button>
            <button class="carousel-nav next" @click="nextSlide">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <polyline points="9 18 15 12 9 6"></polyline>
              </svg>
            </button>
            
            <!-- Carousel Indicators -->
            <div class="carousel-indicators">
              <button 
                v-for="(project, index) in projects" 
                :key="index" 
                @click="goToSlide(index)"
                :class="{ active: currentSlide === index }"
                class="carousel-dot"
              ></button>
            </div>
          </div>
        </div>
      </div>
    </transition>
  </section>
</template>

<script>
import { portfolioImages } from '@/assets/images.js'

export default {
  name: 'PortfolioShowcase',
  data() {
    return {
      showPortfolioModal: false,
      currentSlide: 0,
      projects: [
        {
          name: 'SUNLIGHT APARTMENTS',
          image: portfolioImages.sunlightApartments,
        },
        {
          name: 'BERNARD MYERS HOUSE',
          image: portfolioImages.bernardMyers,
        },
        {
          name: 'VAUXHALL SKY GARDENS',
          image: portfolioImages.vauxhallSky,
        },
        {
          name: 'HOOLA APARTMENTS',
          image: portfolioImages.hoolaApartments,
        },
        {
          name: 'BRONZE APARTMENTS',
          image: portfolioImages.bronzeApartments,
        },
        {
          name: 'CAMBERWELL ON THE GREEN',
          image: portfolioImages.camberwellGreen,
        },
        {
          name: 'VIZON 7 HOLLOWAY',
          image: portfolioImages.vizonHolloway,
        },
        {
          name: 'CITY PENINSULA GREENWICH',
          image: portfolioImages.cityPeninsula,
        },
        {
          name: 'ERNEST WEBSDALE BARKING RIVERSIDE',
          image: portfolioImages.ernestWebsdale,
        },
        {
          name: 'OVAL QUARTER',
          image: portfolioImages.ovalQuarter,
        },
        {
          name: 'BLUEBIRD HOUSE BARKING RIVERSIDE',
          image: portfolioImages.bluebirdHouse,
        },
        {
          name: 'TOTTENHAM HALE',
          image: portfolioImages.tottenhamHale,
        }
      ]
    }
  },
  methods: {
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.projects.length;
    },
    prevSlide() {
      this.currentSlide = (this.currentSlide - 1 + this.projects.length) % this.projects.length;
    },
    goToSlide(index) {
      this.currentSlide = index;
    }
  }
}
</script>

<style scoped>
.portfolio-section {
  padding: 5rem 0;
  background-color: #ffffff;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.section-title {
  font-size: 2.25rem;
  font-weight: 600;
  color: #333;
  margin-bottom: 1rem;
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
  background-color: #4b81b7;
}

.section-description {
  font-size: 1.1rem;
  color: #555;
  margin-bottom: 2.5rem;
  max-width: 800px;
}

/* Bento Box Grid */
.bento-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(2, 250px);
  gap: 1.5rem;
  margin-bottom: 2.5rem;
}

.bento-item {
  border-radius: 8px;
  overflow: hidden;
  position: relative;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.bento-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

/* Item sizes */
.bento-item.large {
  grid-row: span 2;
  grid-column: span 2;
}

.bento-item.medium {
  grid-column: span 2;
}

.bento-item.small {
  grid-column: span 1;
}

.bento-image {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  transition: transform 0.5s ease;
}

.bento-item:hover .bento-image {
  transform: scale(1.05);
}

.bento-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(to top, rgba(0,0,0,0.8), rgba(0,0,0,0));
  padding: 20px;
  color: white;
  transition: background 0.3s ease;
}

.bento-overlay h3 {
  margin: 0;
  font-size: 1.1rem;
  font-weight: 500;
}

/* CTA Button */
.cta-container {
  text-align: center;
  margin-top: 3rem;
}

.cta-button {
  background-color: transparent;
  color: #4b81b7;
  font-weight: 500;
  padding: 12px 25px;
  border: 2px solid #4b81b7;
  text-decoration: none;
  text-transform: uppercase;
  letter-spacing: 1px;
  transition: all 0.3s ease;
  display: inline-block;
  cursor: pointer;
}

.cta-button:hover {
  background-color: #4b81b7;
  color: white;
}

/* Modal Styles */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.75);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 100;
}

.portfolio-modal {
  background-color: white;
  border-radius: 8px;
  width: 95%;
  max-width: 900px;
  height: 80vh;
  max-height: 700px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 24px;
  background-color: #4b81b7;
  color: white;
}

.modal-header h3 {
  margin: 0;
  font-size: 1.5rem;
  font-weight: 600;
}

.close-btn {
  background: transparent;
  border: none;
  color: white;
  cursor: pointer;
  padding: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: opacity 0.3s ease;
}

.close-btn:hover {
  opacity: 0.8;
}

/* Carousel Styles */
.carousel-container {
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.carousel-slides {
  display: flex;
  width: 100%;
  height: 100%;
  transition: transform 0.5s ease;
}

.carousel-slide {
  flex: 0 0 100%;
  height: 100%;
  position: relative;
}

.project-image {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

.project-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(to top, rgba(0,0,0,0.8), rgba(0,0,0,0));
  padding: 30px;
  color: white;
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.3s ease, visibility 0.3s ease;
  z-index: 5;
}

.project-overlay.active-overlay {
  opacity: 1;
  visibility: visible;
}

.project-overlay h3 {
  margin: 0;
  font-size: 1.5rem;
  font-weight: 600;
  text-align: center;
}

.carousel-nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255, 255, 255, 0.5);
  border: none;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  opacity: 0.7;
  transition: opacity 0.3s ease, background 0.3s ease;
  z-index: 10;
}

.carousel-nav:hover {
  opacity: 1;
  background: rgba(255, 255, 255, 0.8);
}

.carousel-nav.prev {
  left: 20px;
}

.carousel-nav.next {
  right: 20px;
}

.carousel-indicators {
  position: absolute;
  bottom: 20px;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  gap: 8px;
  z-index: 10;
}

.carousel-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.5);
  border: none;
  padding: 0;
  cursor: pointer;
  transition: background 0.3s ease;
}

.carousel-dot.active {
  background: white;
}

/* Transitions */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

/* Responsive Design */
@media (max-width: 1024px) {
  .bento-grid {
    grid-template-columns: repeat(3, 1fr);
  }
  
  .bento-item.large {
    grid-column: span 2;
  }
}

@media (max-width: 768px) {
  .section-title {
    font-size: 1.75rem;
    text-align: center;
  }
  
  .section-title:after {
    left: 50%;
    transform: translateX(-50%);
  }
  
  .section-description {
    text-align: center;
    margin-left: auto;
    margin-right: auto;
  }
  
  .bento-grid {
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(3, 200px);
  }
  
  .bento-item.large, .bento-item.medium, .bento-item.small {
    grid-column: span 1;
    grid-row: span 1;
  }
  
  .project-overlay h3 {
    font-size: 1.2rem;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 1.5rem;
  }
  
  .bento-grid {
    grid-template-columns: 1fr;
    grid-template-rows: repeat(6, 180px);
    gap: 1rem;
  }
  
  .carousel-nav {
    width: 35px;
    height: 35px;
  }
  
  .project-overlay {
    padding: 20px;
  }
  
  .project-overlay h3 {
    font-size: 1rem;
  }
}
</style>