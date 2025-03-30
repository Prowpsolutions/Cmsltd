<template>
    <section class="cta-section">
      <div class="cta-container">
        <h3 class="cta-text">Simply contact us for a no obligation, hassle-free quote.</h3>
        <a href="#contact" class="cta-button">CONTACT US</a>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: 'CtaSection'
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
  }
  
  .cta-button:hover {
    background-color: white;
    color: #4b81b7;
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
  }
  </style>