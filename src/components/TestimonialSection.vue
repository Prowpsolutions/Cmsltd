<template>
    <section class="testimonial-section">
      <div class="testimonial-carousel">
        <button class="nav-button prev" @click="prevTestimonial">
          <span>&lt;</span>
        </button>
        
        <div class="testimonial-content">
          <h2>Testimonials</h2>
          <transition name="fade" mode="out-in">
            <div :key="currentIndex" class="testimonial">
              <p class="testimonial-text">{{ currentTestimonial.text }}</p>
              <div class="client-info">
                <p class="client-type">{{ currentTestimonial.clientType }}</p>
                <p class="client-name">{{ currentTestimonial.name }}</p>
              </div>
            </div>
          </transition>
        </div>
        
        <button class="nav-button next" @click="nextTestimonial">
          <span>&gt;</span>
        </button>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: 'TestimonialSection',
    data() {
      return {
        currentIndex: 0,
        testimonials: [
          {
            text: "Thank you to the boys over at HWM for fitting my beautiful new kitchen and bathroom! I couldn't be happier with the end results. Friendly, reliable & trustworthy team. Harry and Leigh always kept us in the loop which we liked. The team working in our house were clean, tidy and very politely - the end results were just perfect... thank you HWM Solutions - Highly recommended!",
            clientType: "PUBLIC CLIENT",
            name: "Claire, Sevenoaks"
          },
          {
            text: "We recently had our entire bathroom remodeled by HWM Solutions and couldn't be more pleased. Their attention to detail and quality of work exceeded our expectations. The project was completed on time and within budget.",
            clientType: "RESIDENTIAL CLIENT",
            name: "James, Tunbridge Wells"
          },
          {
            text: "HWM transformed our outdated office kitchen into a modern, functional space. Their team was professional throughout the process and accommodated our need to keep operations running. Excellent service!",
            clientType: "COMMERCIAL CLIENT",
            name: "TechStart Ltd, London"
          }
        ]
      };
    },
    computed: {
      currentTestimonial() {
        return this.testimonials[this.currentIndex];
      }
    },
    methods: {
      nextTestimonial() {
        this.currentIndex = (this.currentIndex + 1) % this.testimonials.length;
      },
      prevTestimonial() {
        this.currentIndex = (this.currentIndex - 1 + this.testimonials.length) % this.testimonials.length;
      }
    }
  };
  </script>
  
  <style scoped>
  .testimonial-section {
    width: 100%;
    background-color: #ffff;
    position: relative;
    overflow: hidden;
  }
  
  .testimonial-section::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url('/path-to-your-background-image.jpg');
    background-size: cover;
    background-position: center;
    z-index: -1;
  }
  
  .testimonial-carousel {
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 1200px;
    margin: 0 auto;
    padding: 60px 20px;
    min-height: 300px;
  }
  
  .testimonial-content {
    flex: 1;
    max-width: 800px;
    margin: 0 30px;
    text-align: center;
    color: black;
  }
  
  h2 {
    font-size: 2.5rem;
    margin-bottom: 30px;
    font-weight: 500;
  }
  
  .testimonial {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 150px;
  }
  
  .testimonial-text {
    font-size: 1.1rem;
    line-height: 1.6;
    margin-bottom: 30px;
    font-weight: 400;
  }
  
  .client-info {
    margin-top: 20px;
  }
  
  .client-type {
    font-size: 0.9rem;
    font-weight: 600;
    margin-bottom: 5px;
  }
  
  .client-name {
    font-size: 0.9rem;
    font-style: italic;
  }
  
  .nav-button {
    background: none;
    border: none;
    color: #4b81b7;
    font-size: 2rem;
    cursor: pointer;
    padding: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 2;
    transition: opacity 0.3s;
  }
  
  .nav-button:hover {
    opacity: 0.7;
  }
  
  .nav-button:focus {
    outline: none;
  }
  
  /* Transition effects */
  .fade-enter-active, .fade-leave-active {
    transition: opacity 0.5s;
  }
  
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
  
  /* Responsive adjustments */
  @media (max-width: 768px) {
    .testimonial-carousel {
      padding: 40px 10px;
    }
    
    h2 {
      font-size: 2rem;
    }
    
    .testimonial-text {
      font-size: 1rem;
    }
    
    .nav-button {
      font-size: 1.5rem;
    }
  }
  
  /* This is what makes the section adjust based on content */
  .testimonial-content {
    transition: all 0.5s ease;
  }
  </style>