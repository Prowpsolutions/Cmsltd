<template>
    <section class="credits-section">
      <div class="container">
        <h2 class="section-title">Accreditations</h2>
        <div class="credits-logos">
          <div class="logo-item">
            <div class="placeholder-logo">Gas Safe</div>
          </div>
          <div class="logo-item">
            <div class="placeholder-logo">CHAS</div>
          </div>
          <div class="logo-item">
            <div class="placeholder-logo">Life Certificate</div>
          </div>
          <div class="logo-item">
            <div class="placeholder-logo">Checkatrade</div>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: "CreditSection"
  }
  </script>
  
  <style scoped>
  .credits-section {
    padding: 4rem 0;
    background-color: #ffffff;
  }
  
  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1.5rem;
  }
  
  .section-title {
    text-align: center;
    font-size: 2.5rem;
    font-weight: 600;
    color: #333333;
    margin-bottom: 3rem;
  }
  
  .credits-logos {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 2rem;
  }
  
  .logo-item {
    flex: 1;
    min-width: 150px;
    max-width: 200px;
    text-align: center;
  }
  
  .placeholder-logo {
    height: 80px;
    border: 2px dashed #ccc;
    border-radius: 8px;
    background-color: #f5f5f5;
    display: flex;
    justify-content: center;
    align-items: center;
    font-weight: bold;
    color: #777;
    padding: 1rem;
    text-align: center;
    transition: transform 0.3s ease;
  }
  
  .placeholder-logo:hover {
    transform: scale(1.05);
    background-color: #e9e9e9;
  }
  
  @media (max-width: 768px) {
    .credits-logos {
      justify-content: center;
      gap: 2.5rem;
    }
    
    .logo-item {
      flex: 0 0 40%;
    }
    
    .section-title {
      font-size: 2rem;
      margin-bottom: 2rem;
    }
  }
  
  @media (max-width: 480px) {
    .logo-item {
      flex: 0 0 80%;
    }
  }
  </style>