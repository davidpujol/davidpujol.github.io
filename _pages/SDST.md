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
.figure-box {
    margin: 3rem auto;
    text-align: center;
    width: 100%; /* Ensures the container takes the full available width */
    max-width: 900px; /* Limits the size on very large screens to keep it readable */
  }

  .figure-box img {
    width: 100%;       /* Scalable width */
    max-width: 100%;   /* Never wider than its container */
    height: auto;      /* Maintain aspect ratio */
    display: block;
    margin: 0 auto;    /* Center the image */
    border-radius: 4px; /* Optional: matches the clean Hatano aesthetic */
  }

  .figure-caption {
    font-size: 0.95rem;
    color: #555;
    margin-top: 15px;
    font-style: italic;
    line-height: 1.5;
    max-width: 800px;  /* Keeps captions from stretching too wide */
    margin-left: auto;
    margin-right: auto;
  }
  
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
      <a href="https://openaccess.thecvf.com/content/ICCV2025/papers/Pujol-Perich_Sparse-Dense_Side-Tuner_for_efficient_Video_Temporal_Grounding_ICCV_2025_paper.pdf">Paper</a>
      <a href="https://github.com/davidpujol/sparse-dense-side-tuner">Code</a>
      <a href="#bibliography">BibTeX</a>
    </div>
  </div>

  <div class="figure-box">
    <img src="/assets/img/sdst/sdst_efficiency.png" alt="SDST efficiency">
    <div class="figure-caption">Our Sparse-Dense Side-Tuner enables efficient Parameter-Efficient Fine-Tuning (PEFT) for large-scale video temporal grounding models.</div>
  </div>

  <h2 class="section-header">Abstract</h2>
  <p class="content-text">
    Video Temporal Grounding (VTG) involves Moment Retrieval (MR) and Highlight Detection (HD) based on textual queries. For this, most methods rely solely on final-layer features of frozen large pre-trained backbones, limiting their adaptability to new domains. While full fine-tuning is often impractical, parameter-efficient fine-tuning -- and particularly side-tuning (ST) -- has emerged as an effective alternative. However, prior ST approaches this problem from a frame-level refinement perspective, overlooking the inherent sparse nature of MR. To address this, we propose the Sparse-Dense Side-Tuner (SDST), the first anchor-free ST architecture for VTG. We also introduce the Reference-based Deformable Self-Attention, a novel mechanism that enhances the context modeling of the deformable attention -- a key limitation of existing anchor-free methods. Additionally, we present the first effective integration of InternVideo2 backbone into an ST framework, showing its profound implications in performance. Overall, our method significantly improves existing ST methods, achieving highly competitive or SOTA results on QVHighlights, TACoS, and Charades-STA, while reducing up to a 73% the parameter count w.r.t. the existing SOTA methods.
  </p>

<h2 class="section-header">Efficiency through Sparse-Dense Side-Tuning</h2>
  <p class="content-text">
    We propose the <strong>first sparse-dense module for parameter-efficient video grounding</strong>. Our approach relies on <b>Side-Tuning</b>—a paradigm where the heavy video backbone remains completely frozen, and task-specific knowledge is learned through a lightweight parallel network. Unlike standard fine-tuning, which is computationally prohibitive, or traditional adapters that can still be memory-intensive, our side-tuner is specifically designed to be both <strong>time and memory efficient</strong>.
  </p>

  <p class="content-text">
    The module employs a unique <strong>sparse-to-dense strategy</strong>: it first extracts a sparse set of global temporal features to understand the high-level video context, then selectively decodes these into dense moment-level predictions. This separation allows us to leverage the massive representational power of frozen foundation models while training only a fraction of the parameters, enabling state-of-the-art performance on consumer-grade hardware.
  </p>

  <div class="figure-box">
    <img src="/assets/img/sdst/sdst_architecture.png" alt="SDST architecture">
    <div class="figure-caption">Architecture of the Sparse-Dense Side-Tuner: By decoupling the sparse global context from dense temporal refinement, SDST achieves significant efficiency gains over full fine-tuning.</div>
  </div>

  <h2 class="section-header">Performance and Scalability</h2>
  <p class="content-text">
    Evaluation on benchmarks like <strong>Charades-STA</strong> and <strong>ActivityNet Captions</strong> demonstrates that the Sparse-Dense Side-Tuner matches or exceeds the performance of fully fine-tuned models. More importantly, it shows remarkable scalability in terms of memory, time and parameters, allowing for the deployment of VTG systems on hardware with limited resources.
  </p>

  <h2 id="bibliography" class="section-header">Bibliography</h2>
  <pre><code>@inproceedings{pujolperich2025sparse,
  title={Sparse-Dense Side-Tuner for Efficient Video Temporal Grounding},
  author={Pujol-Perich, David and Escalera, Sergio and Clapés, Albert},
  booktitle={Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV)},
  year={2025}
}</code></pre>

</div>