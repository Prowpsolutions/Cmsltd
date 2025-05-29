<template>
    <section class="about-section">
      <div class="container">
        <div class="about-container">
          <div class="about-content">
            <h2 class="section-title">About Us</h2>
            
            <div class="about-text">
              <p>
                Capital Maintenance and Support Services Ltd was founded in 2020 with a specific focus on
                providing high-quality property maintenance services to a variety of clients, including
                residential and commercial managing agents, landlords, freeholders, retailers, hospitality
                providers, insurers, and policyholders.
              </p>
              <p>
                We offer a wide range of in-house services, which sets us apart from our competitors, and
                our single source service delivery is something that is not matched by others in the industry.
                Our clients can rely on us to handle all aspects of their property maintenance needs, from
                start to finish, without having to deal with multiple vendors or contractors.
              </p>
            </div>
            
            <div class="contact-details">
              <div class="contact-item">
                <div class="contact-icon">
                  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07 19.5 19.5 0 01-6-6 19.79 19.79 0 01-3.07-8.67A2 2 0 014.11 2h3a2 2 0 012 1.72 12.84 12.84 0 00.7 2.81 2 2 0 01-.45 2.11L8.09 9.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45 12.84 12.84 0 002.81.7A2 2 0 0122 16.92z" />
                  </svg>
                </div>
                <div class="contact-info">
                  <h4>TELEPHONE</h4>
                  <div class="copy-container">
                    <a href="tel:02035762392" class="copy-text" @click.prevent="copyToClipboard('02035762392')">0203 576 2392</a>
                    <div class="tooltip" :class="{ 'show-tooltip': tooltipPhone }">Copied!</div>
                  </div>
                </div>
              </div>
              
              <div class="contact-item">
                <div class="contact-icon">
                  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z" />
                    <polyline points="22,6 12,13 2,6" />
                  </svg>
                </div>
                <div class="contact-info">
                  <h4>EMAIL</h4>
                  <div class="copy-container">
                    <a href="mailto:info@cmsservicesltd.com" class="copy-text" @click.prevent="copyToClipboard('info@cmsservicesltd.com')">info@cmsservicesltd.com</a>
                    <div class="tooltip" :class="{ 'show-tooltip': tooltipEmail }">Copied!</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          
          <div class="about-image-container">
            <div class="about-image">
              <img src="../assets/maintenance.png" alt="Capital Maintenance and Support Services" />
            </div>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: 'AboutUsSection',
    data() {
      return {
        tooltipPhone: false,
        tooltipEmail: false
      }
    },
    methods: {
      copyToClipboard(text) {
        navigator.clipboard.writeText(text)
          .then(() => {
            // Show the appropriate tooltip
            if (text.includes('@')) {
              this.tooltipEmail = true;
              setTimeout(() => {
                this.tooltipEmail = false;
              }, 2000);
            } else {
              this.tooltipPhone = true;
              setTimeout(() => {
                this.tooltipPhone = false;
              }, 2000);
            }
          })
          .catch(err => {
            console.error('Could not copy text: ', err);
          });
      }
    }
  }
  </script>
  
  <style scoped>
  .about-section {
    padding: 5rem 0;
  }
  
  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1rem;
  }
  
  .about-container {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 3rem;
  }
  
  .about-content {
    flex: 1;
    min-width: 300px;
  }
  
  .section-title {
    font-size: 2.25rem;
    font-weight: 600;
    color: #333;
    margin-bottom: 1.5rem;
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
    background-color: #4a6cf7;
  }
  
  .about-text {
    margin-bottom: 2rem;
  }
  
  .about-text p {
    margin-bottom: 1rem;
    font-size: 1.05rem;
    line-height: 1.7;
    color: #555;
  }
  
  .contact-details {
    display: flex;
    flex-wrap: wrap;
    gap: 2rem;
    margin-top: 2rem;
  }
  
  .contact-item {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
  }
  
  .contact-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 50px;
    height: 50px;
    background-color: #4a6cf7;
    border-radius: 50%;
    color: white;
  }
  
  .contact-info h4 {
    font-size: 0.9rem;
    font-weight: 600;
    color: #777;
    margin: 0 0 0.5rem 0;
    letter-spacing: 1px;
  }
  
  .copy-container {
    position: relative;
    display: inline-block;
  }
  
  .copy-text {
    color: #333;
    font-size: 1.1rem;
    font-weight: 600;
    text-decoration: none;
    transition: color 0.3s ease;
    cursor: pointer;
    display: inline-flex;
    align-items: center;
  }
  
  .copy-text:after {
    content: '';
    display: inline-block;
    background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="%234a6cf7" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="13" height="13" rx="2" ry="2"></rect><path d="M5 15H4a2 2 0 01-2-2V4a2 2 0 012-2h9a2 2 0 012 2v1"></path></svg>');
    width: 16px;
    height: 16px;
    margin-left: 8px;
    opacity: 0;
    transition: opacity 0.3s ease;
  }
  
  .copy-text:hover:after {
    opacity: 1;
  }
  
  .copy-text:hover {
    color: #4a6cf7;
  }
  
  .tooltip {
    position: absolute;
    background-color: #4a6cf7;
    color: white;
    padding: 4px 8px;
    border-radius: 4px;
    font-size: 12px;
    bottom: 100%;
    left: 50%;
    transform: translateX(-50%) translateY(5px);
    opacity: 0;
    visibility: hidden;
    transition: opacity 0.3s ease, transform 0.3s ease, visibility 0.3s;
    white-space: nowrap;
    pointer-events: none;
  }
  
  .tooltip:after {
    content: '';
    position: absolute;
    top: 100%;
    left: 50%;
    margin-left: -5px;
    border-width: 5px;
    border-style: solid;
    border-color: #4a6cf7 transparent transparent transparent;
  }
  
  .show-tooltip {
    opacity: 1;
    visibility: visible;
    transform: translateX(-50%) translateY(0);
  }
  
  .about-image-container {
    flex: 1;
    min-width: 300px;
  }
  
  .about-image {
    position: relative;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
  }
  
  .about-image:before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(74, 108, 247, 0.1);
    z-index: 1;
  }
  
  .about-image img {
    width: 100%;
    height: auto;
    display: block;
  }
  
  @media (max-width: 768px) {
    .about-section {
      padding: 3rem 0;
    }
    
    .about-container {
      flex-direction: column-reverse;
      gap: 2rem;
    }
    
    .section-title {
      font-size: 1.75rem;
    }
    
    .contact-details {
      flex-direction: column;
      gap: 1.5rem;
    }
  }
  
  @media (max-width: 480px) {
    .section-title {
      font-size: 1.5rem;
    }
    
    .about-text p {
      font-size: 1rem;
    }
  }
  </style>