<template>
    <section class="service-section">
      <div class="container">
        <div class="service-grid">
          <div v-for="service in services" :key="service.id" class="service-card">
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
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: 'ServiceSection',
    data() {
      return {
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
          }
        ]
      }
    }
  }
  </script>
  
  <style scoped>
  .service-section {
    padding: 4rem 0;
    background-color: #ffffff;
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
  }
  </style>