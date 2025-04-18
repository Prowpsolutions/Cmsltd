<template>
  <section class="cta-section">
    <div class="cta-container">
      <h3 class="cta-text">Simply contact us for a no obligation, hassle-free quote.</h3>
      <a @click.prevent="showContactForm = true" href="#contact" class="cta-button">CONTACT US</a>
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
export default {
  name: 'CtaSection',
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
    }
  }
}
</script>

<style scoped>
.cta-section {
  width: 100%;
  background-color: #4b81b7;
  padding: 30px 0;
}

.cta-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  flex-wrap: wrap;
}

.cta-text {
  color: white;
  font-size: 1.4rem;
  font-weight: 500;
  margin: 0;
  flex: 1;
  min-width: 200px;
  text-align: center;
}

.cta-button {
  background-color: transparent;
  color: white;
  font-weight: 500;
  padding: 12px 25px;
  border: 2px solid white;
  text-decoration: none;
  text-transform: uppercase;
  letter-spacing: 1px;
  transition: all 0.3s ease;
  display: inline-block;
  margin: 15px 0 15px 20px;
  cursor: pointer;
}

.cta-button:hover {
  background-color: white;
  color: #4b81b7;
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

@media (max-width: 768px) {
  .cta-container {
    flex-direction: column;
    text-align: center;
  }
  
  .cta-text {
    margin-bottom: 20px;
  }
  
  .cta-button {
    margin: 10px 0;
  }
  
  .modal-container {
    width: 90%;
    margin: 0 16px;
  }
}
</style>