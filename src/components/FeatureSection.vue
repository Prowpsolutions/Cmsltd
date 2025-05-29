<template>
  <section class="feature-section">
    <div class="feature-container">
      <!-- First Feature Block -->
      <div class="feature-block" ref="featureBlock1">
        <div class="feature-image" ref="featureImage1">
          <!-- Use placeholder image until real image is available -->
          <div class="placeholder-image">
             <img src="../assets/feature.png" alt="Capital Maintenance and Support Services" />
            <span>Team Image</span>
          </div>
        </div>
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
          <a @click.prevent="showContactForm = true" href="#contact" class="cta-button">CONTACT US</a>
        </div>
      </div>
      
      <!-- Second Feature Block (Image left, text right) -->
      <div class="feature-block" ref="featureBlock2">
        <div class="feature-image" ref="featureImage2">
          <!-- Use placeholder image until real image is available -->
          <div class="placeholder-image">
            <img src="../assets/feature2.png" alt="Capital Maintenance and Support Services" />
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
          <a @click.prevent="showContactForm = true" href="#contact" class="cta-button">CONTACT US</a>
        </div>
      </div>
    </div>

    <!-- Contact Form Modal -->
    <transition name="fade">
      <div v-if="showContactForm" class="modal-overlay" @click.self="showContactForm = false">
        <div class="modal-container">
          <div class="modal-header">
            <h3>Contact Us</h3>
            <button @click="showContactForm = false" class="close-btn">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="6" x2="6" y2="18"></line>
                <line x1="6" y1="6" x2="18" y2="18"></line>
              </svg>
            </button>
          </div>
          <form @submit.prevent="submitForm" class="contact-form">
            <div class="form-group">
              <label for="name">Name</label>
              <input 
                type="text" 
                id="name" 
                v-model="formData.name" 
                placeholder="Enter your name"
                required
              />
            </div>
            <div class="form-group">
              <label for="phone">Phone Number</label>
              <input 
                type="tel" 
                id="phone" 
                v-model="formData.phone" 
                placeholder="Enter your phone number"
                required
              />
            </div>
            <div class="form-group">
              <label for="email">Email</label>
              <input 
                type="email" 
                id="email" 
                v-model="formData.email" 
                placeholder="Enter your email address"
                required
              />
            </div>
            <div class="form-group">
              <label for="message">Message</label>
              <textarea 
                id="message" 
                v-model="formData.message" 
                rows="4" 
                placeholder="How can we help you?"
                required
              ></textarea>
            </div>
            <button type="submit" class="submit-btn">Send Message</button>
          </form>
        </div>
      </div>
    </transition>
  </section>
</template>

<script>
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

export default {
  name: 'FeatureSection',
  data() {
    return {
      showContactForm: false,
      formData: {
        name: '',
        phone: '',
        email: '',
        message: ''
      }
    }
  },
  mounted() {
    this.initAnimations();
  },
  methods: {
    submitForm() {
      // Here you would typically handle the form submission
      // e.g., send to your backend or email service
      console.log('Form submitted:', this.formData);
      
      // Reset form data
      this.formData = {
        name: '',
        phone: '',
        email: '',
        message: ''
      };
      
      // Close modal
      this.showContactForm = false;
      
      // You could add a success notification here
    },
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
    }
  }
}
</script>

<style scoped>
.feature-section {
  width: 100%;
  max-width: 100%;
  margin: 0 auto;
  padding: 4rem 2rem;
  background-color: #ffffff;
}

.feature-container {
  max-width: 1200px;
  margin: 0 auto;
}

.feature-block {
  display: flex;
  align-items: center;
  margin-bottom: 6rem;
  gap: 4rem;
}

/* Alternate the text/image order on desktop */
.feature-block:nth-child(odd) {
  flex-direction: row-reverse;
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
  color: #000000;
  margin-bottom: 1.5rem;
  font-weight: 600;
}

.feature-description {
  font-size: 1rem;
  line-height: 1.6;
  color: #333333;
  margin-bottom: 1.5rem;
}

/* CTA Button Style - Exactly matching the CTA Section */
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

/* Modal styles */
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

.modal-container {
  background-color: white;
  border-radius: 8px;
  width: 100%;
  max-width: 500px;
  padding: 0;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
  overflow: hidden;
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

.contact-form {
  padding: 24px;
}

.form-group {
  margin-bottom: 20px;
}

.form-group label {
  display: block;
  margin-bottom: 6px;
  font-weight: 500;
  color: #333;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 12px 16px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
  transition: border 0.3s ease;
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: #4b81b7;
  outline: none;
}

.submit-btn {
  background-color: #4b81b7;
  color: white;
  border: none;
  padding: 12px 24px;
  font-size: 1rem;
  font-weight: 600;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.3s ease;
  width: 100%;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.submit-btn:hover {
  background-color: #3a70a6;
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(75, 129, 183, 0.2);
}

.submit-btn:active {
  transform: translateY(0);
}

/* Transitions */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

/* Improved Responsive Styles */
@media (max-width: 768px) {
  .feature-section {
    padding: 4rem 2rem; /* Keep consistent with desktop padding */
  }
  
  .feature-block {
    flex-direction: column !important; /* Override any other flex direction */
    gap: 2.5rem;
    margin-bottom: 5rem;
  }
  
  /* Make all images appear with the same style and size */
  .feature-image {
    width: 100%; /* Make image container full width */
    margin-bottom: 1rem;
  }
  
  .feature-title {
    font-size: 2rem;
    text-align: center;
  }
  
  .feature-description {
    text-align: center;
  }
  
  .feature-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
  }
  
  .placeholder-image {
    height: 220px;
    width: 100%;
  }
  
  .cta-button {
    padding: 0.75rem 2rem;
  }
  
  .modal-container {
    width: 90%;
    margin: 0 16px;
  }
}

/* Extra small devices */
@media (max-width: 480px) {
  .feature-section {
    padding: 3rem 1.5rem; /* Slightly reduced but still proportional */
  }
  
  .feature-block {
    margin-bottom: 4rem;
    gap: 2rem;
  }
  
  .feature-title {
    font-size: 1.75rem;
  }
  
  .feature-description {
    font-size: 0.95rem;
    max-width: 90%;
    margin-left: auto;
    margin-right: auto;
  }
  
  .cta-button {
    width: auto;
    min-width: 200px;
    justify-content: center;
    padding: 0.75rem 1.5rem;
  }
  
  .placeholder-image {
    height: 180px;
  }
}
</style>