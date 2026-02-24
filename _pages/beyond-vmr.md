---
layout: page
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
  .bibtex-box { background: #f9f9f9; padding: 20px; border-radius: 8px; font-family: monospace; font-size: 0.9rem; overflow-x: auto; border: 1px solid #eee; }
</style>

<div class="container" style="max-width: 860px;">
  
  <div class="project-header">
    <h1 class="project-title">Beyond Caption-Based Queries for Video Moment Retrieval</h1>
    <div class="authors">
      <strong>David Pujol-Perich</strong><sup>1,2,3</sup>, Albert Clapés<sup>1,2</sup>, Dima Damen<sup>3</sup>, Sergio Escalera<sup>1,2</sup>, Michael Wray<sup>3</sup>
    </div>
    <div class="affiliations">
      <sup>1</sup>University of Barcelona &nbsp;&nbsp;<sup>2</sup>Computer Vision Center &nbsp;&nbsp; <sup>3</sup>University of Bristol
    </div>
    <div class="venue" style="font-weight: 600; font-size: 1.3rem; color: #b31b1b; margin-top: 10px;">CVPR 2026</div>
    
    <div class="pill-links">
      <a href="#">Paper</a>
      <a href="#">Code</a>
      <a href="#bibliography">BibTeX</a>
    </div>
  </div>

  <div class="figure-box">
    <img src="/assets/img/beyond_vmr/motivation.png" alt="Difference between caption-based and search-based queries">
    <div class="figure-caption">We identify a significant domain gap between the descriptive captions used in VMR training and the actual search patterns of real users.</div>
  </div>

  <h2 class="section-header">Abstract</h2>
  <p class="content-text">
Current Video Moment Retrieval (VMR) models are trained on videos paired with captions, which are written by annotators after watching the videos. These captions are used as textual queries---which we term caption-based queries. This annotation process induces a visual bias, leading to overly descriptive and fine-grained queries, which significantly differ from the more general search queries that users are likely to employ in practice.

In this work, we investigate the degradation of existing VMR methods, particularly of DETR architectures, when trained on caption-based queries but evaluated on search queries. For this, we introduce three benchmarks by modifying the textual queries in three public VMR datasets---i.e., HD-EPIC, YouCook2 and ActivityNet-Captions. Our analysis reveals two key generalization challenges: (i) A language gap, arising from the linguistic under-specification of search-queries, and (ii) a multi-moment gap, caused by the shift from single moment to multi-moment queries. We also identify a critical issue in these architectures---an active decoder-query collapse---as a primary cause of the poor generalization to multi-moment instances. We mitigate this issue with architectural modifications that effectively increase the number of active decoder queries. Extensive experiments demonstrate that our approach improves performance on search queries by up to 14.82%, and up to 21.83% mAp_m on multi-moment search queries.
  </p>

  <h2 class="section-header">Captions vs. Realistic Search Queries</h2>
  <p class="content-text">
    Standard VMR benchmarks like EpicKitchens or Charades use captions that describe every visual detail (e.g., <i>"The person picks up a silver spoon with their right hand from the wooden table"</i>). In contrast, search logs reveal that humans often use minimal, under-specified queries (e.g., <i>"taking a spoon"</i>). Our analysis shows that VMR performance drops by up to 40% when moving from captions to these realistic search distributions.
  </p>

  <h2 class="section-header">Automated Under-specification Pipeline</h2>
  <p class="content-text">
    To simulate realistic user behavior without manual re-annotation, we propose an <strong>automated under-specification pipeline</strong>. By leveraging an LLM-driven scheme, we systematically remove visually biased modifiers (color, material, specific spatial relations) while preserving the core action-object intent.
  </p>
  <div class="figure-box">
    <img src="/assets/img/beyond_vmr/pipeline.png" alt="Under-specification pipeline">
    <div class="figure-caption">Our pipeline reduces caption complexity to match the linguistic distribution of real-world search logs.</div>
  </div>

<h2 class="section-header">Architectural Modifications</h2>
  <p class="content-text">
    We identify that current DETR-based VMR models suffer from <strong>active decoder-query collapse</strong>, where only a small subset of the learnable queries contributes to predictions. While common in object detection, this is exacerbated in VMR by the single-moment prior of existing benchmarks. Our modifications target two specific failure modes:
  </p>

  <div style="margin-bottom: 1.5rem;">
    <p class="content-text" style="margin-bottom: 0.5rem;">
      <strong>Self-Attention Removal (-SA):</strong> We remove the self-attention mechanisms in the decoder to eliminate <i>coordination collapse</i>. This prevents queries from becoming overly synchronized, allowing them to independently specialize for different temporal moments.
    </p>
    <p class="content-text">
      <strong>Decoder-Query Dropout (+QD):</strong> We introduce a stochastic dropout regularizer for the decoder queries to prevent <i>index collapse</i>. This forces the model to distribute information across a broader range of available learnable queries.
    </p>
  </div>

  <p class="content-text">
    Combined, these modifications—<strong>-SA+QD</strong>—effectively double the number of active decoder queries in some cases, significantly improving retrieval performance on under-specified search queries.
  </p>

<h2 class="section-header">Qualitative Results</h2>
<p class="content-text">
  Our qualitative analysis on the <strong>HD-EPIC-S2</strong> and <strong>YC2-S</strong> benchmarks reveals that standard models like CG-DETR often struggle to retrieve all relevant segments for under-specified queries. This is primarily because these models only activate a limited number of queries, failing to capture the full temporal extent of the action.
</p>

<div style="margin-bottom: 2rem;">
  <p class="content-text" style="margin-bottom: 0.8rem;">
    <strong>Multi-Moment Coverage:</strong> In scenarios containing multiple ground-truth (GT) moments, base models typically suffer from query sparsity—for instance, activating only two queries to retrieve three distinct moments, leaving valid segments localized incorrectly or missed entirely.
  </p>
  <p class="content-text">
    <strong>Improved Retrieval Diversity:</strong> By removing self-attention and introducing query dropout (<strong>-SA+QD</strong>), our model encourages a larger number of diverse queries to activate. This leads to significantly better coverage and localization for general search queries such as <i>"Wash grapes"</i> or <i>"Add ingredients"</i>, where the model must identify multiple occurrences of the same action.
  </p>
</div>

  <div class="figure-box">
    <img src="/assets/img/beyond_vmr/qualitative_results.png" alt="Qualitative results for HD-EPIC-S1 and HD-EPIC-S3">

    <div class="figure-caption">Comparison of localized moments between caption-based and search-based queries for HD-EPIC-S1 and HD-EPIC-S3.</div>
  </div>

  <h2 id="bibliography" class="section-header">Bibliography</h2>
  <div class="bibtex-box">
  </div>

</div>