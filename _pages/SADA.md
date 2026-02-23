---
layout: page
permalink: /sada/
nav: false
nav_order: 2
display_categories: [work, fun]
horizontal: false
---
<style>
  body { background-color: #ffffff !important; color: #000000 !important; }
  .project-header { text-align: center; padding: 4rem 0 2rem; }
  .project-title { font-size: 2.4rem; font-weight: 800; color: #000; margin-bottom: 1rem; line-height: 1.2; }
  .authors { font-size: 1.25rem; margin-bottom: 0.5rem; }
  .affiliations { font-size: 1.05rem; color: #555; margin-bottom: 2rem; }
  
  .pill-links { display: flex; justify-content: center; gap: 10px; flex-wrap: wrap; margin-bottom: 3rem; }
  .pill-links a { 
    border: 1.5px solid #000; color: #000; border-radius: 30px; 
    padding: 8px 24px; font-weight: 600; transition: 0.3s; 
  }
  .pill-links a:hover { background: #000; color: #fff; text-decoration: none; }
  
  .section-header { font-size: 1.8rem; font-weight: 700; margin: 4rem 0 1.5rem; border-bottom: 2px solid #000; padding-bottom: 10px; }
  .content-text { font-size: 1.1rem; line-height: 1.8; color: #111; text-align: justify; margin-bottom: 1.5rem; }
  
  .figure-box { margin: 3rem 0; text-align: center; }
  .figure-box img { max-width: 100%; height: auto; border-radius: 4px; }
  .figure-caption { font-size: 0.95rem; color: #555; margin-top: 15px; font-style: italic; }
  
  pre { background: #f4f4f4; padding: 20px; border-radius: 8px; font-family: monospace; font-size: 0.9rem; border: 1px solid #ddd; }
</style>

<div class="container" style="max-width: 860px; background-color: white;">
  
  <div class="project-header">
    <h1 class="project-title">SADA: Semantic Adversarial Unsupervised Domain Adaptation for Temporal Action Localization</h1>
    <div class="authors">
      <strong>David Pujol-Perich</strong>, Albert Clapés, Sergio Escalera
    </div>
    <div class="affiliations">
      University of Barcelona and Computer Vision Center, Spain
    </div>
    <div class="venue" style="font-weight: 700; font-size: 1.4rem; color: #000; margin-top: 10px;">WACV 2025</div>
    
    <div class="pill-links">
      <a href="https://openaccess.thecvf.com/content/WACV2025/papers/Pujol-Perich_SADA_Semantic_Adversarial_Unsupervised_Domain_Adaptation_for_Temporal_Action_Localization_WACV_2025_paper.pdf">Paper</a>
      <a href="https://github.com/davidpujol/SADA">Code</a>
      <a href="#bibliography">BibTeX</a>
    </div>
  </div>

  <div class="figure-box">
    
    <div class="figure-caption">SADA tackles the performance degradation of Temporal Action Localization (TAL) in real-world applications with unseen domains.</div>
  </div>

  <h2 class="section-header">Abstract</h2>
  <p class="content-text">
Temporal Action Localization (TAL) is a complex task that poses relevant challenges, particularly when attempting to generalize on new -- unseen -- domains in real-world applications. These scenarios, despite realistic, are often neglected in the literature, exposing these solutions to important performance degradation. In this work, we tackle this issue by introducing, for the first time, an approach for Unsupervised Domain Adaptation (UDA) in sparse TAL, which we refer to as Semantic Adversarial unsupervised Domain Adaptation (SADA). Our contributions are threefold: (1) we pioneer the development of a domain adaptation model that operates on realistic sparse action detection benchmarks; (2) we tackle the limitations of global-distribution alignment techniques by introducing a novel adversarial loss that is sensitive to local class distributions, ensuring finer-grained adaptation; and (3) we present a novel set of benchmarks based on EpicKitchens100 and CharadesEgo, that evaluate multiple domain shifts in a comprehensive manner. Our experiments indicate that SADA improves the adaptation across domains when compared to fully supervised state-of-the-art and alternative UDA methods, attaining a performance boost of up to 6.14 mAP.
  </p>

  <h2 class="section-header">Addressing Feature Misalignment</h2>
  <p class="content-text">
    Traditional UDA methods align domain distributions globally, which often leads to "feature misalignment" where specific actions from the source domain are incorrectly mapped to different actions in the target domain. Our proposed <strong>SADA loss</strong> overcomes this limitation by aligning each action's distribution across both domains individually. This finer-grained adaptation ensures that the semantic boundaries of actions are preserved even under significant domain shifts.
  </p>
  
  <div class="figure-box">
    <img src="/assets/img/sada/sada_loss.png" alt="SADA loss mechanism">
    <div class="figure-caption">By aligning individual action distributions, SADA prevents the collapse of class-specific features during domain adaptation.</div>
  </div>

  <h2 class="section-header">New Benchmarking Setups</h2>
  <p class="content-text">
    Real-world video understanding requires handling sparse action detection and intersecting labels. Since existing benchmarks were inadequate, we propose a comprehensive suite of <strong>6 new benchmarks based on EpicKitchens-100</strong>. These setups examine both appearance and acquisition domain shifts, providing a robust framework for assessing a model's adaptability to diverse environments.
  </p>
  
  <div class="figure-box">
    <img src="/assets/img/sada/benchmarks.png" alt="EpicKitchens-100 UDA Benchmarks">
    <div class="figure-caption">Overview of the proposed benchmarks examining various types of domain shifts in sparse TAL.</div>
  </div>

  <h2 id="bibliography" class="section-header">Bibliography</h2>
  <pre><code>@InProceedings{Pujol-Perich_2025_WACV,
    author    = {Pujol-Perich, David and Clap{\'e}s, Albert and Escalera, Sergio},
    title     = {SADA: Semantic Adversarial Unsupervised Domain Adaptation for Temporal Action Localization},
    booktitle = {Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision (WACV)},
    month     = {January},
    year      = {2025}
}</code></pre>

</div>