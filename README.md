# week_3_internship

# Internship Progress – Week 3

## Revising Computer Vision & LangChain, and Exploring Segmentation Models

---

## Overview

In Week 3 of my internship, I focused on revising **computer vision fundamentals** and **LangChain concepts** before working on the project problem statement. As part of the task, I was asked to explore possible **segmentation models** and **embedding models** that could be used for solving the problem.

During this week, most of my effort went into understanding and experimenting with **segmentation models**, while getting an initial understanding of how embedding models fit into the overall approach.

---

## Tasks Assigned

- Revise core **computer vision concepts**
- Revise basic **LangChain concepts**
- Understand the problem statement and think through solution approaches
- Explore suitable **segmentation models**
- Get an overview of **embedding models**
- Document observations and learnings

---

## What I Worked On

### Computer Vision Revision  
I revisited important computer vision topics such as image processing, object detection, and instance segmentation. This helped me better understand how segmentation models work and how their outputs can be used in the project.

---

### LangChain Concepts Revision  
I revised the basics of **LangChain**, including how chains are structured and how embeddings and retrieval workflows are generally used. This helped me understand where LangChain fits into the overall system design.

---

### Segmentation Model Exploration

I explored different segmentation models to understand their behavior and practical usability.

#### **Mask R-CNN**
- Used for player segmentation
- Produced segmentation masks but was slow in execution
- Missed certain visual details in some cases
- Less suitable for the project needs

#### **YOLOv8-Seg**
- Explored as an alternative segmentation approach
- Faster compared to Mask R-CNN
- Preserved important visual features more consistently
- Appeared to be more practical for the project

### Segment Anything Model (SAM)

When SAM was released, it looked very promising because of the quality of its segmentation masks. I did try to work with SAM, but I quickly ran into practical issues.

The model is very heavy in terms of checkpoint size and memory usage. Running it repeatedly on multiple images was not feasible on my setup. In addition, SAM is not designed for fully automated pipelines and often requires prompts or extra logic to consistently segment only the player.

Because of these reasons, even though the segmentation quality is high, SAM was not practical for this project.


### Cascade Mask R-CNN

From reading research papers, I learned that Cascade Mask R-CNN improves accuracy by refining predictions in multiple stages. However, this also makes the model even slower than standard Mask R-CNN.

Since I had already observed that Mask R-CNN was slow and sometimes removed important features like helmets, it was clear that Cascade Mask R-CNN would only make these issues worse. Therefore, it was not implemented.


### YOLACT / YOLACT++

YOLACT models are often described as real-time instance segmentation approaches. From the literature, I found that they achieve speed by simplifying the mask generation process.

The downside of this trade-off is that the resulting masks can be coarse. Small but important details, such as helmets or player equipment, are sometimes lost. For this project, losing even a small feature can affect player identification accuracy, which made YOLACT unsuitable.


### SOLO / SOLOv2

SOLO-based models remove the concept of bounding boxes and directly predict instance masks. While this approach is interesting, papers show that these models struggle when objects overlap or when there are large variations in scale.

Since cricket images often contain overlapping players and varying camera angles, SOLO-based models were not reliable for this use case.


## Final Takeaway

Instead of implementing many models and encountering the same limitations repeatedly, I focused on understanding their drawbacks first. By studying research papers and testing models where possible, it became clear which approaches would not fit the project requirements.

YOLOv8-seg was ultimately chosen not because it is popular, but because it offers the best balance between speed, feature preservation, and practical usability for this task.


Based on these observations, **YOLOv8-Seg** seemed more suitable for the problem requirements.

---

### 🔹 Embedding Models (Overview)
Along with segmentation, I also gained a basic understanding of **embedding models** and how they are generally used for feature representation and similarity-based tasks. This helped me see how segmentation and embeddings work together in the overall solution.

---

## 🎯 Key Learnings

- Strengthened understanding of **computer vision fundamentals**
- Gained practical insight into **segmentation models**
- Learned how to compare models based on speed and output quality
- Revised essential **LangChain concepts**
- Understood the role of embeddings in the project workflow

---

## 📖 Summary

Week 3 was focused on revising foundational concepts and exploring different model options for the project. By revisiting computer vision and LangChain concepts and experimenting with segmentation models, I gained clarity on how these components fit into the overall solution.

---

## 📌 Tech Stack / Concepts

- Computer Vision  
- Segmentation Models  
- LangChain  
- Python  
