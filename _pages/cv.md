---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Education
======

* M.S. in University of California, San Diego, 2024 - present
* B.S. in Zhejiang University, Hangzhou, 2020 - 2024

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
<!-- Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>
   -->
   
Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>


Intern experience
======


Research Roles
------
* Nov 2024 - Present: Research Intern (M.S. Student)
  * **Lab: Su Lab, University of California, San Diego (UCSD)**
  * **Duties included:**
    * Lead implementation and evaluation for the ManiTaskGen project, focusing on Embodied AI and VLM.
    * Developed a novel hybrid task generator that synthesizes comprehensive mobile manipulation tasks using receptacle-aware 3D scene graphs and VLM voting.
    * Responsible for agent performance optimization, including the design and application of inference-time techniques (RFT optimization) to improve VLM agent reliability in complex 3D environments. (See Publications for full results.)
  * **Supervisor:** Prof. Hao Su (Primary Advisor), and Liu Dai (Day-to-day Mentor)

* Apr 2023 - Jun 2024: Research Assistant (B.S. Student)
  * **Lab: ZLST Lab, Zhejiang University (ZJU)**
  * **Duties included:**
    * Conducted theoretical and applied research on graph recommendation algorithms (MF, LightGCN), specifically addressing the long-tail effect and exposure bias.
    * Developed and implemented specialized deviation correction loss functions to enhance algorithmic fairness and quality.
    * Responsible for full lifecycle model establishment, hyperparameter tuning, and performance validation using a multi-dimensional model structure.
  * **Supervisor:** Prof. Can Wang (Primary Advisor), and Jiawei Chen (Day-to-day Mentor)

Industry & Engineering Roles
------
* Feb 2024 - Jun 2024: Software Development Engineer, Machine Learning Platform, Hangzhou
  * **Company: Bytedance Co.**
  * **Duties included:** Conducted in-depth analysis of model execution traces across heterogeneous GPU architectures to quantify performance bottlenecks (memory, computation, IO). Provided data-driven deployment recommendations to improve resource allocation efficiency.
  * **Supervisor:** Chenliaohui Fang

* Jul 2022 - Aug 2022: Technical Developer Intern, Technical Department, Beijing
  * **Company: Light Chaser Animation Co.**
  * **Duties included:** Analyzed rendering binding codes involving advanced graphics (follicle nodes, inverse kinematics). Supported animation motion capture and assisted in internal cloud platform research to resolve cooperative pain points (e.g., file format alignment).
  * **Supervisor:** Huiman Hou

* Jul 2022 - Sep 2022: Quant Intern, Alpha Quant Strategy Team, Remote
  * **Company: Huatai Securities Co., Ltd.**
  * **Duties included:** Analyzed advanced quantitative research reports. Used Python to successfully reproduce and verify the results, including 29 analytical tables and 9 figures from timing strategy reports, demonstrating strong data reproduction, visualization, and quantitative analysis skills.
  * **Supervisor:** Kang He

Honors
======
* Contests (ACM/ICPC/CCPC)
  * Gold Medal of the 2021 China Collegiate Programming Contest Asia East Contests, Weihai, Nov 2022
  * Gold Medal of the 2021 International Collegiate Programming Contest Asia East Contests, Kunming, Apr 2022
  * Gold Medal of the 2021 International Collegiate Programming Contest Asia East Contests, Jinan, Nov 2021
  * Gold Medal of the 2021 International Collegiate Programming Contest Asia East Contests, Kunming, Apr 2021
  * Gold Medal of the 2020 International Collegiate Programming Contest Asia East Contests, Yinchuan, May 2021

* Scholarship
  * 2nd Prize Academic Scholarship of Zhejiang University in Oct 2021, Oct 2023 (8%)
  * 2nd Prize ND Scholarship of Zhejiang University Education Foundation in Oct 2021 (7/735)

  
Skills
======
* **Programming:** C/C++ (6 yrs), Python (4 yrs), algorithms & data structures
* **AI/ML:** PyTorch, Vision-Language Models (VLM), Embodied AI, deep learning frameworks
* **Systems:** GPU optimization, parallel computing, MLOps, performance analysis
* **Graphics:** OpenGL, B-spline curves, computer graphics, digital image processing




<div class="cv-download-links">
  <a href="{{ base_path }}/files/cv.pdf" class="btn btn--primary">Download CV PDF</a>
</div>



<!-- Service and leadership
======
* Currently signed in to 43 different slack teams -->
