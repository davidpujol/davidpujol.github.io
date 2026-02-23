---
layout: page
permalink: /sdst/
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
    <h1 class="project-title">Sparse-Dense Side-Tuner for Efficient Video Temporal Grounding</h1>
    <div class="authors">
      <strong>David Pujol-Perich</strong>, Sergio Escalera, Albert Clapés
    </div>
    <div class="affiliations">
      University of Barcelona and Computer Vision Center, Spain
    </div>
    <div class="venue" style="font-weight: 700; font-size: 1.4rem; color: #000; margin-top: 10px;">ICCV 2025</div>
    
    <div class="pill-links">
      <a href="https://arxiv.org/abs/2507.07744">Paper (arXiv)</a>
      <a href="https://github.com/davidpujol/sparse-dense-side-tuner">Code</a>
      <a href="#bibliography">BibTeX</a>
    </div>
  </div>

  <div class="figure-box">
    
    <div class="figure-caption">Our Sparse-Dense Side-Tuner enables efficient Parameter-Efficient Fine-Tuning (PEFT) for large-scale video temporal grounding models.</div>
  </div>

  <h2 class="section-header">Abstract</h2>
  <p class="content-text">
    Video Temporal Grounding (VTG) requires models to localize specific moments in long videos based on natural language queries. While large-scale pre-trained models have set new benchmarks, fine-tuning them for VTG is computationally expensive. We propose the <strong>Sparse-Dense Side-Tuner</strong>, a parameter-efficient architecture that bridges the gap between high-level semantic features and dense temporal predictions. By training a lightweight side-network alongside a frozen backbone, we achieve state-of-the-art results while significantly reducing the number of trainable parameters and training time.
  </p>

  <h2 class="section-header">Efficiency through Side-Tuning</h2>
  <p class="content-text">
    The core of our approach is the separation of the heavy feature extraction (frozen backbone) from the task-specific grounding logic (side-tuner). Unlike standard fine-tuning or simple adapters, our side-tuner utilizes a <strong>sparse-to-dense strategy</strong>: it selectively processes sparse temporal samples to capture global context before refining them into dense moment predictions. This allows the model to maintain the rich representations of the backbone while specializing for the high-precision requirements of temporal grounding.
  </p>
  
  <div class="figure-box">
    
    <div class="figure-caption">Comparison between full fine-tuning and our Sparse-Dense Side-Tuning approach, highlighting the reduction in trainable parameters.</div>
  </div>

  <h2 class="section-header">Sparsity vs. Density</h2>
  <p class="content-text">
    Temporal grounding is inherently multi-scale. A model must understand the global video structure (sparse) while precisely pinpointing start/end times (dense). Our architecture introduces a cross-attention mechanism that allows the side-tuner to query the frozen backbone at varying temporal resolutions. This dual-pathway ensures that the model remains efficient without sacrificing the granularity needed to distinguish between similar actions in a long sequence.
  </p>

  <h2 class="section-header">Performance and Scalability</h2>
  <p class="content-text">
    Evaluation on benchmarks like <strong>Charades-STA</strong> and <strong>ActivityNet Captions</strong> demonstrates that the Sparse-Dense Side-Tuner matches or exceeds the performance of fully fine-tuned models. More importantly, it shows remarkable scalability, allowing for the deployment of VTG systems on hardware with limited GPU memory.
  </p>
  
  <div class="figure-box">
    
    <div class="figure-caption">Inference speed and parameter count comparison showing the efficiency gains of our proposed method.</div>
  </div>

  <h2 id="bibliography" class="section-header">Bibliography</h2>
  <pre><code>@inproceedings{pujolperich2025sparse,
  title={Sparse-Dense Side-Tuner for Efficient Video Temporal Grounding},
  author={Pujol-Perich, David and Escalera, Sergio and Clapés, Albert},
  booktitle={Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV)},
  year={2025}
}</code></pre>

</div>