<template>
    <section class="feature-section">
      <!-- First Feature Block -->
      <div class="feature-block" ref="featureBlock1">
        <div class="feature-content" ref="featureContent1">
          <h2 class="feature-title">Transform your living space</h2>
          <p class="feature-description">
            HWM Solutions provide a wide range of professional construction and building maintenance services for both
            commercial and residential clients across London and the South East.
          </p>
          <p class="feature-description">
            Whatever your needs, our specialist teams can manage any building requirement – from large office developments, home
            extensions and renovations, to maintenance, decoration work, 24/7 emergency repairs and much more.
          </p>
          <button class="contact-button">
            Contact Us
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M5 12h14"></path>
              <path d="M12 5l7 7-7 7"></path>
            </svg>
          </button>
        </div>
        <div class="feature-image" ref="featureImage1">
          <!-- Use placeholder image until real image is available -->
          <div class="placeholder-image">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
              <circle cx="8.5" cy="8.5" r="1.5"></circle>
              <polyline points="21 15 16 10 5 21"></polyline>
            </svg>
            <span>Team Image</span>
          </div>
        </div>
      </div>
      
      <!-- Second Feature Block (Image left, text right) -->
      <div class="feature-block" ref="featureBlock2">
        <div class="feature-image" ref="featureImage2">
          <!-- Use placeholder image until real image is available -->
          <div class="placeholder-image">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
              <circle cx="8.5" cy="8.5" r="1.5"></circle>
              <polyline points="21 15 16 10 5 21"></polyline>
            </svg>
            <span>Construction Image</span>
          </div>
        </div>
        <div class="feature-content" ref="featureContent2">
          <h2 class="feature-title">High quality results</h2>
          <p class="feature-description">
            We have extensive knowledge, experience, and a vast skill set within our team - offering you a complete end-to-end
            solution, and total peace of mind.
          </p>
          <p class="feature-description">
            With a large and diverse portfolio of successful projects, we pride ourselves on providing exceptional customer care –
            working closely with all our clients throughout to support them and deliver only the highest quality results.
          </p>
          <button class="contact-button projects-button">
            Our Projects
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M5 12h14"></path>
              <path d="M12 5l7 7-7 7"></path>
            </svg>
          </button>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  import { gsap } from 'gsap';
  import { ScrollTrigger } from 'gsap/ScrollTrigger';
  
  gsap.registerPlugin(ScrollTrigger);
  
  export default {
    name: 'FeatureSection',
    mounted() {
      this.initAnimations();
    },
    methods: {
      initAnimations() {
        // Animation for first block
        this.animateBlock(
          this.$refs.featureBlock1, 
          this.$refs.featureContent1, 
          this.$refs.featureImage1,
          false
        );
        
        // Animation for second block
        this.animateBlock(
          this.$refs.featureBlock2, 
          this.$refs.featureContent2, 
          this.$refs.featureImage2,
          true
        );
      },
      animateBlock(blockRef, contentRef, imageRef, isReversed = false) {
        // Create a timeline for this block
        const tl = gsap.timeline({
          scrollTrigger: {
            trigger: blockRef,
            start: "top 80%",
            end: "bottom 20%",
            toggleActions: "play none none none"
          }
        });
  
        // Initial states
        gsap.set(contentRef, { 
          opacity: 0,
          x: isReversed ? 50 : -50
        });
        
        gsap.set(imageRef, { 
          opacity: 0,
          x: isReversed ? -50 : 50,
          scale: 0.95
        });
  
        // Animation sequence
        tl.to(contentRef, {
          opacity: 1,
          x: 0,
          duration: 0.8,
          ease: "power2.out"
        })
        .to(imageRef, {
          opacity: 1,
          x: 0,
          scale: 1,
          duration: 0.8,
          ease: "power2.out"
        }, "-=0.5");
        
        // Add hover animations for buttons
        if (contentRef.querySelector('.contact-button')) {
          const button = contentRef.querySelector('.contact-button');
          
          button.addEventListener('mouseenter', () => {
            gsap.to(button, {
              backgroundColor: button.classList.contains('projects-button') ? '#5a6268' : '#0056b3',
              scale: 1.05,
              duration: 0.3
            });
            
            gsap.to(button.querySelector('svg'), {
              x: 4,
              duration: 0.3
            });
          });
          
          button.addEventListener('mouseleave', () => {
            gsap.to(button, {
              backgroundColor: button.classList.contains('projects-button') ? '#6c757d' : '#007bff',
              scale: 1,
              duration: 0.3
            });
            
            gsap.to(button.querySelector('svg'), {
              x: 0,
              duration: 0.3
            });
          });
        }
      }
    }
  }
  </script>
  
  <style scoped>
  .feature-section {
    max-width: 1200px;
    margin: 0 auto;
    padding: 4rem 2rem;
  }
  
  .feature-block {
    display: flex;
    align-items: center;
    margin-bottom: 6rem;
    gap: 4rem;
  }
  
  .feature-content {
    flex: 1;
  }
  
  .feature-image {
    flex: 1;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  }
  
  .placeholder-image {
    width: 100%;
    height: 300px;
    background-color: #f2f2f2;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: #888;
    border-radius: 4px;
  }
  
  .placeholder-image svg {
    margin-bottom: 1rem;
    width: 48px;
    height: 48px;
    color: #aaa;
  }
  
  .placeholder-image span {
    font-size: 1rem;
  }
  
  .feature-title {
    font-size: 2.5rem;
    color: #333;
    margin-bottom: 1.5rem;
    font-weight: 600;
  }
  
  .feature-description {
    font-size: 1rem;
    line-height: 1.6;
    color: #666;
    margin-bottom: 1.5rem;
  }
  
  .contact-button {
    display: inline-flex;
    align-items: center;
    padding: 0.75rem 1.5rem;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 1rem;
    cursor: pointer;
    transition: all 0.3s ease;
    font-weight: 500;
    gap: 0.5rem;
  }
  
  .projects-button {
    background-color: #6c757d;
  }
  
  .contact-button svg {
    transition: transform 0.3s;
  }
  
  /* Responsive Styles */
  @media (max-width: 768px) {
    .feature-block {
      flex-direction: column;
      gap: 2rem;
    }
    
    .feature-title {
      font-size: 2rem;
    }
  }
  </style>