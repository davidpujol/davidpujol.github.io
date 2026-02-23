---
layout: page
title: Beyond Caption-Based Queries in Video Moment Retrieval
permalink: /beyond-vmr/
nav: false
nav_order: 2
display_categories: [work, fun]
horizontal: false
---
<style>
  .project-header { text-align: center; padding: 4rem 0 2rem; }
  .project-title { font-size: 2.4rem; font-weight: 800; color: #222; margin-bottom: 1rem; }
  .authors { font-size: 1.2rem; margin-bottom: 0.5rem; }
  .affiliations { font-size: 1.05rem; color: #666; margin-bottom: 2rem; }
  .pill-links { display: flex; justify-content: center; gap: 10px; flex-wrap: wrap; margin-bottom: 3rem; }
  .pill-links a { 
    border: 1px solid #444; color: #444; border-radius: 30px; 
    padding: 6px 20px; font-weight: 500; transition: 0.2s; 
  }
  .pill-links a:hover { background: #444; color: #fff; text-decoration: none; }
  
  .section-header { font-size: 1.8rem; font-weight: 700; margin: 4rem 0 1.5rem; border-bottom: 1px solid #eaeaea; padding-bottom: 10px; }
  .content-text { font-size: 1.1rem; line-height: 1.8; color: #333; text-align: justify; margin-bottom: 1.5rem; }
  .figure-box { margin: 2.5rem 0; text-align: center; }
  .figure-caption { font-size: 0.95rem; color: #666; margin-top: 15px; font-style: italic; }
  
  .bibtex-box { background: #f9f9f9; padding: 20px; border-radius: 8px; font-family: monospace; font-size: 0.9rem; overflow-x: auto; border: 1px solid #eee; }
</style>

<div class="container" style="max-width: 860px;">
  
  <div class="project-header">
    <h1 class="project-title">Beyond Caption-Based Queries for Video Moment Retrieval</h1>
    <div class="authors">
      <strong>David Pujol-Perich</strong><sup>1*</sup>, Albert Clapés<sup>1*</sup>, Dima Damen<sup>2</sup>, Sergio Escalera<sup>1</sup>, Michael Wray<sup>2</sup>
    </div>
    <div class="affiliations">
      <sup>1</sup>University of Barcelona &nbsp;&nbsp; <sup>2</sup>University of Bristol
      <br><small>*Equal Contribution</small>
    </div>
    <div class="venue" style="font-weight: 600; font-size: 1.3rem; color: #b31b1b; margin-top: 10px;">CVPR 2026</div>
    
    <div class="pill-links">
      <a href="#">Paper</a>
      <a href="https://github.com/davidpujol/beyond-vmr">Code</a>
      <a href="#">ArXiv</a>
      <a href="#bibliography">BibTeX</a>
    </div>
  </div>

  <div class="figure-box">
    
    <div class="figure-caption">We identify a significant domain gap between the descriptive captions used in VMR training and the actual search patterns of real users.</div>
  </div>

  <h2 class="section-header">Abstract</h2>
  <p class="content-text">
    Current Video Moment Retrieval (VMR) models are primarily trained on videos paired with captions written by annotators after watching the video. This process induces a "visual bias," leading to overly descriptive and fine-grained queries that differ significantly from the more general search queries users employ in practice. In this work, we investigate the degradation of existing VMR methods when evaluated on realistic search queries. We introduce an automated under-specification pipeline to generate three new benchmarks—<strong>HD-EPIC-S1/S2, ANC-S, and YC2-S</strong>—demonstrating that current architectural designs struggle to bridge the gap between high-level intent and visual grounding.
  </p>

  <h2 class="section-header">Captions vs. Realistic Search Queries</h2>
  <p class="content-text">
    Standard VMR benchmarks like EpicKitchens or Charades use captions that describe every visual detail (e.g., <i>"The person picks up a silver spoon with their right hand from the wooden table"</i>). In contrast, search logs reveal that humans use minimal, under-specified queries (e.g., <i>"taking a spoon"</i>). Our analysis shows that VMR performance drops by up to 40% when moving from captions to these realistic search distributions.
  </p>

  <h2 class="section-header">Automated Under-specification Pipeline</h2>
  <p class="content-text">
    To simulate realistic user behavior without manual re-annotation, we propose an <strong>automated under-specification pipeline</strong>. By leveraging dependency parsing and LLM-driven pruning, we systematically remove visually biased modifiers (color, material, specific spatial relations) while preserving the core action-object intent.
  </p>
  <div class="figure-box">
    
    <div class="figure-caption">Our pipeline reduces caption complexity to match the linguistic distribution of real-world search logs.</div>
  </div>

  <h2 class="section-header">Architectural Modifications</h2>
  <p class="content-text">
    We explore how modifications to the grounding mechanism—such as <strong>Adaptive Score Refinement (ASR)</strong> and multi-scale temporal modeling—affect the model's ability to handle semantic sparsity. We find that while these modifications improve standard VMR, they are insufficient for bridging the gap to under-specified queries, suggesting a need for better latent space alignment between sparse text and dense video features.
  </p>
  <div class="figure-box">
    
    <div class="figure-caption">Evaluated architectures include modified DETR-based and anchor-free models like Flash-VTG.</div>
  </div>

  <h2 class="section-header">Qualitative Results</h2>
  <p class="content-text">
    Our qualitative analysis reveals that models often "over-fit" to descriptive words. For example, when "silver" is removed from a query, the model fails to localize the spoon entirely, even if the action remains clear. The following examples showcase the retrieval success and failure cases on our new HD-EPIC-S1/S2 benchmarks.
  </p>
  <div class="figure-box">
    
    <div class="figure-caption">Comparison of localized moments between caption-based and search-based queries.</div>
  </div>

  <h2 id="bibliography" class="section-header">Bibliography</h2>
  <div class="bibtex-box">
@inproceedings{pujol2026beyond,
  title={Beyond Caption-Based Queries for Video Moment Retrieval},
  author={Pujol-Perich, David and Clapés, Albert and Damen, Dima and Escalera, Sergio and Wray, Michael},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  year={2026}
}</div>

</div>