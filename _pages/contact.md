---
layout: default
title: Contact
permalink: /contact/
---

<div class="contact-container">
  <h1 class="page-title"><span class="section-icon">✉️</span> Contact Information</h1>
  
  <div class="contact-grid">
    <div class="contact-card">
      <div class="contact-icon">
        <i class="fas fa-envelope"></i>
      </div>
      <h3>Email</h3>
      <p><a href="mailto:ykiaras@emory.edu">ykiaras@emory.edu</a></p>
    </div>
    
    <div class="contact-card">
      <div class="contact-icon">
        <i class="fas fa-building"></i>
      </div>
      <h3>Office Address</h3>
      <p>
        Emory University<br>
        Department of Biomedical Informatics<br>
        Clifford Lab<br>
        101 Woodruff Circle<br>
        Atlanta, GA 30322
      </p>
    </div>
  </div>
  
  <div class="profiles-section">
    <h2>Professional Profiles</h2>
    <div class="profiles-grid">
      <a href="https://scholar.google.com/citations?user=1WWKzTEAAAAJ&hl=en&authuser=1" class="profile-link" target="_blank">
        <i class="ai ai-google-scholar"></i>
        <span>Google Scholar</span>
      </a>
      
      <a href="https://orcid.org/0009-0004-4903-6298" class="profile-link" target="_blank">
        <i class="ai ai-orcid"></i>
        <span>ORCID</span>
      </a>
      
      <a href="https://www.ncbi.nlm.nih.gov/myncbi/yashar.kiarashinejad.1/bibliography/public/" class="profile-link" target="_blank">
        <i class="ai ai-pubmed"></i>
        <span>PubMed</span>
      </a>
      
      <a href="https://www.linkedin.com/in/yashar-kiarashinejad/" class="profile-link" target="_blank">
        <i class="fab fa-linkedin"></i>
        <span>LinkedIn</span>
      </a>
      
      <a href="https://github.com/YashKia" class="profile-link" target="_blank">
        <i class="fab fa-github"></i>
        <span>GitHub</span>
      </a>
    </div>
  </div>
  
  <div class="collaboration-section">
    <h2>Research Collaboration</h2>
    <p>I am interested in collaborations in the following areas:</p>
    <ul class="collaboration-list">
      <li>AI applications in healthcare</li>
      <li>Wearable technology for neurological disorders</li>
      <li>Privacy-preserving edge computing for health monitoring</li>
      <li>Sleep analysis and behavior prediction</li>
    </ul>
    <p class="contact-invitation">
      If you're interested in collaboration or have questions about my research, please don't hesitate to reach out via email.
    </p>
  </div>
</div>

<style>
  /* Purple Color Spectrum */
  :root {
    --light-purple: #BDB5D5;     /* Light purple for backgrounds */
    --medium-purple: #9E95B7;    /* Medium purple for hover states */
    --darker-purple: #7D6E96;    /* Darker purple for text for better readability */
    --darkest-purple: #4A3A69;   /* Darkest purple for emphasis */
  }

  .contact-container {
    max-width: 800px;
    margin: 0 auto;
    padding: 2em 1em;
  }
  
  .page-title {
    font-size: 2.2em;
    color: var(--darker-purple);
    margin-bottom: 1.5em;
    text-align: center;
  }
  
  .section-icon {
    margin-right: 0.5em;
  }
  
  .contact-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2em;
    margin-bottom: 3em;
  }
  
  .contact-card {
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.05);
    padding: 2em;
    text-align: center;
    transition: transform 0.3s ease;
  }
  
  .contact-card:hover {
    transform: translateY(-5px);
  }
  
  .contact-icon {
    font-size: 2.5em;
    color: var(--light-purple);
    margin-bottom: 0.5em;
  }
  
  .contact-card h3 {
    color: var(--darkest-purple);
    margin-bottom: 0.5em;
  }
  
  .contact-card p {
    color: #555;
    line-height: 1.6;
  }
  
  .contact-card a {
    color: var(--darker-purple);
    text-decoration: none;
    font-weight: 500;
  }
  
  .contact-card a:hover {
    color: var(--darkest-purple);
  }
  
  .profiles-section {
    margin-bottom: 3em;
  }
  
  .profiles-section h2 {
    text-align: center;
    margin-bottom: 1.5em;
    color: var(--darkest-purple);
  }
  
  .profiles-grid {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 1.5em;
  }
  
  .profile-link {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-decoration: none;
    color: #444;
    transition: transform 0.3s ease;
    width: 120px;
  }
  
  .profile-link:hover {
    transform: translateY(-5px);
    color: var(--darker-purple);
  }
  
  .profile-link i {
    font-size: 2.5em;
    margin-bottom: 0.5em;
    color: var(--light-purple);
  }
  
  .collaboration-section {
    background-color: #f9f9f9;
    padding: 2em;
    border-radius: 8px;
    margin-top: 2em;
    border-left: 4px solid var(--light-purple);
  }
  
  .collaboration-section h2 {
    color: var(--darker-purple);
    margin-bottom: 1em;
  }
  
  .collaboration-list {
    margin-left: 2em;
    margin-bottom: 1.5em;
  }
  
  .collaboration-list li {
    margin-bottom: 0.5em;
    color: #555;
  }
  
  .contact-invitation {
    font-weight: 500;
    color: var(--darkest-purple);
    text-align: center;
    margin-top: 1.5em;
  }
  
  @media (max-width: 768px) {
    .contact-grid {
      grid-template-columns: 1fr;
    }
  }
</style>

<!-- Add Font Awesome and Academicons for icons -->
<script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/jpswalsh/academicons@1/css/academicons.min.css"> 