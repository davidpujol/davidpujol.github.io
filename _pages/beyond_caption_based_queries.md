---
layout: page
title: SADA:Semantic adversarial unsupervised domain adaptation for Temporal Action Localization
permalink: /sada/
nav: false
nav_order: 2
display_categories: [work, fun]
horizontal: false
---

<!-- pages/projects.md -->
<div class="authors" style="text-align: center;">
  <h4>David Pujol-Perich, Albert Clapés, and Sergio Escalera</h4>
  <h4>University of Barcelona and Computer Vision Center, Spain</h4>
</div>
<div class="row justify-content-center">
    <div class="col-sm-12">
      
      <p class="text-center mt-3" style="font-size: 0.95rem; color: #444;">
        <em>Current VMR models are trained on hyper-descriptive captions (left), but fail on realistic, under-specified user search queries (right). We bridge this gap with three new benchmarks.</em>
      </p>
    </div>
  </div>

  <div class="row mt-5">
    <div class="col-md-12">
      <h2 class="font-weight-bold">Abstract</h2>
      <p style="text-align: justify; line-height: 1.7;">
        Current Video Moment Retrieval (VMR) models are trained on videos paired with captions written by annotators after watching the video. This process induces a <strong>visual bias</strong>, leading to overly descriptive queries that significantly differ from real-world search behavior. We investigate the degradation of VMR methods on realistic queries and introduce three benchmarks: <strong>HD-EPIC-S1/S2, ANC-S, and YC2-S</strong>. We demonstrate that this performance gap is architecture-agnostic and show that fine-tuning with our generated queries significantly improves real-world generalization.
      </p>
    </div>
  </div>

  <div class="row mt-5">
    <div class="col-md-12">
      <h2 class="font-weight-bold">The Under-specification Pipeline</h2>
      <p>
        We propose an automated pipeline that utilizes Large Language Models (LLMs) and dependency parsing to strip "visual bias" from captions. This preserves the core semantic intent while mimicking the sparsity of human search queries.
      </p>
      <div class="text-center py-3">
        
      </div>
    </div>
  </div>

  <div class="row mt-5">
    <div class="col-md-12">
      <h2 class="font-weight-bold">Is the Gap Architecture-Agnostic?</h2>
      <p>
        Yes. We evaluated both DETR-based and non-DETR models like <strong>Flash-VTG</strong>. Even models with multi-scale temporal modeling struggle with semantic sparsity, proving that the visual bias is a data distribution challenge rather than a decoder limitation.
      </p>
      
    </div>
  </div>

  <div class="row mt-5">
    <div class="col-md-12">
      <h2 class="font-weight-bold">User Realism Study</h2>
      <p>
        We conducted a study with 22 participants who rated our generated queries. Our HD-EPIC-S1 benchmark achieved a <strong>89% realism score</strong>, confirming that our automated pipeline effectively simulates actual user behavior.
      </p>
    </div>
  </div>

  <div class="row mt-5 mb-5" id="bibtex">
    <div class="col-md-12">
      <h2 class="font-weight-bold">BibTeX</h2>
      <pre style="background: #f8f9fa; padding: 20px; border-radius: 8px; border: 1px solid #eee;"><code>@inproceedings{pujol2026beyond,
  title={Beyond Caption-Based Queries for Video Moment Retrieval},
  author={Pujol-Perich, David and Clapés, Albert and Damen, Dima and Escalera, Sergio and Wray, Michael},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  year={2026}
}</code></pre>
    </div>
  </div>

</div>