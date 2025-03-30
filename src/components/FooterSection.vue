<template>
    <footer class="footer-section">
      <div class="footer-container">
        <div class="footer-left">
          <a href="/privacy-policy" class="footer-link">Privacy Policy</a> | HWM Solutions {{ currentYear }} &copy;
        </div>
        <div class="footer-right">
          Web Development by <a href="/index.html" class="footer-link">Nerdwares <span class="resknow-logo">N</span></a>
        </div>
      </div>
    </footer>
  </template>
  
  <script>
  export default {
    name: 'FooterSection',
    computed: {
      currentYear() {
        return new Date().getFullYear();
      }
    }
  }
  </script>
  
  <style scoped>
  .footer-section {
    width: 100%;
    background-color: #2b2d36;
    padding: 20px 0;
    color: white;
  }
  
  .footer-container {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
  }
  
  .footer-link {
    color: white;
    text-decoration: none;
    transition: opacity 0.3s ease;
  }
  
  .footer-link:hover {
    opacity: 0.8;
  }
  
  .resknow-logo {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    background-color: white;
    color: #2b2d36;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    font-weight: bold;
    font-size: 14px;
    margin-left: 3px;
  }
  
  @media (max-width: 768px) {
    .footer-container {
      flex-direction: column;
      text-align: center;
    }
    
    .footer-left, .footer-right {
      margin: 5px 0;
    }
  }
  </style>