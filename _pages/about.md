---
permalink: /
title: ""
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

<div class="about-container">
  <div class="research-overview">
    <h2><span class="section-icon">🔬</span> Research Overview</h2>

    <p style="text-align: justify;"> 
    As a postdoctoral researcher at the <a href="https://gdclifford.info/gari">Clifford Lab</a> at Emory University, my research focuses on developing novel AI-driven methods and sensing technologies to address critical challenges in healthcare, particularly for neurological and developmental disorders. My interdisciplinary approach combines expertise in artificial intelligence, biomedical sensing, and signal processing to create tools that can improve patient outcomes through early detection and personalized interventions.
    </p>

    <div class="research-areas">
      <h3>Research Focus Areas</h3>
      
      <div class="research-area">
        <h4><span class="area-icon">🧠</span> Novel Biomarkers for Neurological Disorders</h4>
        <p>Working with the <a href="https://empowerment.emory.edu">Cognitive Empowerment Program</a> and the <a href="https://alzheimers.emory.edu">Goizueta Alzheimer's Disease Research Center</a>, I develop methods to identify cognitive markers in older adults at risk for Mild Cognitive Impairment using multimodal data from wearable technologies, including <a href="https://www.nextsense.io">NextSense in-ear EEG devices</a> and wristband health monitors.</p>
      </div>
      
      <div class="research-area">
        <h4><span class="area-icon">🔐</span> Privacy-Preserving Sensing for Neurodevelopmental Disorders</h4>
        <p>In collaboration with <a href="https://thecenterfordiscovery.org">The Center for Discovery</a>, I am researching the relationship between sleep patterns and behavioral outcomes in children with autism spectrum disorder. This work involves building an end-to-end edge computing system using off-body sensors that prioritizes privacy while extracting meaningful behavioral insights.</p>
      </div>
      
      <div class="research-area">
        <h4><span class="area-icon">📊</span> AI-Driven Pattern Recognition for Health Monitoring</h4>
        <p>Building on my PhD research in knowledge discovery at Georgia Tech, I develop interpretable machine learning models for biomedical applications. This includes work on the <a href="https://moody-challenge.physionet.org/2022/">George B. Moody PhysioNet Challenge</a>, co-organizing a challenge with over 80 participants on heart murmur detection from phonocardiogram recordings.</p>
      </div>
    </div>

    <p>Before joining Emory, I completed my PhD at Georgia Tech (2016-2021) where I focused on machine learning-assisted optimization and knowledge discovery in nanophotonics. My doctoral research developed new approaches using deep learning, manifold learning, and dimensionality reduction to better understand light-matter interactions.</p>
  </div>

  <div class="news-section">
    <h2><span class="section-icon">📰</span> Recent News</h2>
    <ul class="news-list">
      <li class="news-item">
        <span class="news-date">Apr 2025</span>
        <div class="news-content">
          Yashar gave a talk in Profound Autism Summit "<strong>Predicting High-Risk Behaviors in Individuals with Profound Autism Using Sleep and Other Environmental Factors</strong>" <a href="https://behaviorlive.com/events/predicting-high-risk-behaviors-in-individuals-with-profound-autism-using-sleep-an">presentation link</a>
        </div>
      </li>
      
      <li class="news-item">
        <span class="news-date">Feb 2025</span>
        <div class="news-content">
          Our paper titled "<strong>Feasibility of Assessing Cognitive Impairment via Distributed Camera Network and Privacy‐Preserving Edge Computing</strong>" has been published in <strong>Alzheimer's & Dementia: Diagnosis, Assessment & Disease Monitoring</strong>. <a href="https://pmc.ncbi.nlm.nih.gov/articles/PMC11848627/">Read paper</a>
        </div>
      </li>
      
      <li class="news-item">
        <span class="news-date">Feb 2025</span>
        <div class="news-content">
          Yashar gave a talk in CTSA Lunch and Learn Series on "<strong>Can Sleep Architecture and Behavior Patterns Predict Next-Day Challenging Behavior in Autism?</strong>"
        </div>
      </li>
      
      <li class="news-item">
        <span class="news-date">Jan 2025</span>
        <div class="news-content">
          Our paper titled "<strong>From Motion to Emotion: Exploring Challenging Behaviors in Autism Spectrum Disorder Through Analysis of Wearable Physiology and Movement</strong>" has been published in <strong>Physiological Measurements</strong>. <a href="https://iopscience.iop.org/article/10.1088/1361-6579/ada51b/meta">Read paper</a>
        </div>
      </li>
      
      <li class="news-item">
        <span class="news-date">Oct 2024</span>
        <div class="news-content">
          Our paper titled "<strong>Off-body Sleep Analysis for Predicting Adverse Behavior in Individuals with Autism Spectrum Disorder</strong>" has been published in <strong>IEEE Journal of Biomedical and Health Informatics</strong>. <a href="https://ieeexplore.ieee.org/abstract/document/10669162">Read paper</a>
        </div>
      </li>
      
      <li class="news-item">
        <span class="news-date">Jul 2024</span>
        <div class="news-content">
          Yashar has been awarded the <strong>Thrasher Research Fund Early Career Award</strong> for the project titled "<strong>Enhancing Behavioral Understandings and Interventions in Children with Autism Spectrum Disorder using Artificial Intelligence.</strong>" <a href="https://www.thrasherresearch.org/grant/02384?lang=eng">More details</a>
        </div>
      </li>
    </ul>
  </div>
</div>

<style>
  /* Purple Color Spectrum */
  :root {
    --light-purple: #BDB5D5;     /* Light purple for backgrounds */
    --medium-purple: #9E95B7;    /* Medium purple for hover states */
    --darker-purple: #7D6E96;    /* Darker purple for text */
    --darkest-purple: #4A3A69;   /* Darkest purple for emphasis */
    --text-color: #333;          /* Black for regular text */
    --light-text: #555;          /* Lighter black for secondary text */
  }

  .about-container {
    max-width: 900px;
    margin: 0 auto;
  }
  
  .section-icon, .area-icon {
    margin-right: 0.5em;
  }
  
  .research-overview {
    margin-top: 1em;
    margin-bottom: 3em;
  }
  
  .research-areas {
    margin: 2em 0;
  }
  
  .research-area {
    margin-bottom: 1.5em;
    background-color: #f9f9f9;
    border-radius: 8px;
    padding: 1.5em;
    border-left: 4px solid var(--light-purple);
  }
  
  .research-area h4 {
    margin-top: 0;
    color: var(--darker-purple);
  }
  
  .news-section {
    margin-top: 3em;
  }
  
  .news-list {
    list-style: none;
    padding: 0;
  }
  
  .news-item {
    display: flex;
    margin-bottom: 1.5em;
    padding-bottom: 1.5em;
    border-bottom: 1px solid #eee;
  }
  
  .news-date {
    min-width: 100px;
    font-weight: bold;
    color: var(--light-text);
  }
  
  .news-content {
    flex: 1;
    color: var(--text-color);
  }

  h2 {
    color: var(--darker-purple);
  }

  h3 {
    color: var(--darker-purple);
  }
  
  @media (max-width: 768px) {
    .news-item {
      flex-direction: column;
    }
    
    .news-date {
      margin-bottom: 0.5em;
    }
  }
</style>
