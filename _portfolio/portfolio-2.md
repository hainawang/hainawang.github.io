---
title: "🎨 SIGGRAPH 2016 Reproduction: Rough Sketch Simplification"  
excerpt: "Complete reproduction and critical analysis of Simo-Serra et al.'s rough sketch simplification paper; includes Lua/Torch to Python/PyTorch migration, loss function validation, and dataset construction experiments.<br/><img src='/images/reproduction_teaser.jpg'>"
slidesurl: '../files/roughsketch_slides.pdf'
paperurl: '../files/siggraph2016_reproduction.pdf'
collection: portfolio
---





## **Project Summary**

* **Original Paper:** Rough sketch simplification (Simo-Serra et al., SIGGRAPH 2016)
* **Goal:** Fully reproduce the key results of the paper, including rewriting the original Lua/Torch code base into modern Python/PyTorch.
* **Core Contribution:** Re-implemented the Fully Convolutional Network (FCN) architecture, constructed comparable datasets, and designed targeted comparison experiments to validate the necessity of the paper's key technical components.
* **Technologies:** Python, PyTorch, Computer Vision (CV), Deep Learning Architecture Analysis.
* **Authors:** Haina Wang, Yixuan Pu
* **Institution:** Zhejiang University.

---

## **Technical Re-implementation & Challenges**

The primary task was translating the original codebase from Lua/Torch (a framework popular in 2016) to a modern Python/PyTorch environment.

### **Code Conversion**
Successfully translated the paper's network structure and logic, simplifying components that are now standard (e.g., Batch Normalization and the ADADELTA optimizer) into modern PyTorch layers.

### **Loss Function Vectorization** 
The original paper utilized a highly localized loss map (M) based on a normalized histogram H(I,u,v). Implementing this loss calculation efficiently in Python required a clever solution to avoid slow loops: we vectorized the calculation by generating multiple shifted image maps, calculating contributions, and aggregating them using `numpy.select()`. This required strong attention to efficient low-level code structure.

### **Result Verification**
Successfully reran and compared our Python-generated output against all major figures shown in the original paper, achieving acceptable performance.

---

## **Critical Analysis & Validation Experiments**

Beyond simple reproduction, we designed new experiments to critically test the paper's claimed novelty and best practices.

### **1. Validating the Custom Loss Function**

The paper introduced a weighted loss map M to emphasize certain areas during training. We ran comparative training experiments:

* **Experiment:** Training with the custom loss map (w/M) vs. training with standard Mean Squared Error (MSE) only (w/oM).
* **Finding:** The comparison confirmed that the custom loss map significantly accelerated convergence and improved the clarity of the lines in the initial training phases (Iterations 50-200), validating the author's decision to use it.

### **2. Analyzing the Inverse Dataset Construction**

The authors created their dataset by adding noise to clean sketches ("Inverse Dataset Generation"). We tested the sensitivity of this approach by constructing multiple datasets:

* **Manual vs. Automated Noise:** We compared training on the authors' preferred "limited manual noise" (slur, tone) dataset against datasets generated from common cartoon images (ATD-12K).
  * **Finding:** Our test confirmed that the model trained on general cartoon images struggled, highlighting that the manual noise and clean context provided by the Inverse Dataset were crucial for obtaining a high-quality result.

* **Patches Importance:** We tested training with and without randomly extracted fixed-size patches.
  * **Finding:** The use of small, random patches dramatically accelerated the training process by effectively eliminating large blank spaces and improving feature density.

---

## **Technical Challenges and Reflections**

This project highlighted core challenges in reproducing academic work across different programming paradigms:

* **Framework Migration:** Converting from Lua/Torch to Python/PyTorch required understanding both the original implementation details and modern deep learning best practices.
* **Performance Optimization:** Vectorizing the custom loss function calculation was crucial for training efficiency, demonstrating the importance of low-level optimization in deep learning pipelines.
* **Experimental Design:** Designing controlled experiments to validate specific claims required careful isolation of variables and systematic comparison methodologies.

---

## **Conclusion**

This project demonstrated my ability to engage with complex academic literature, re-engineer solutions across different programming paradigms (Lua to Python), and use scientific rigor to validate core research claims through comparative experimentation. While the ML architecture of the 2016 paper has since been surpassed by modern models (e.g., Vision Transformers), the pioneering approach to dataset construction remains highly influential in Computer Graphics and artistic AI today.

---

> **Citation:** Reproduction study of Simo-Serra et al. "Learning to Simplify: Fully Convolutional Networks for Rough Sketch Cleanup." *SIGGRAPH 2016*. Implementation and analysis by Haina Wang, Yixuan Pu (2023).