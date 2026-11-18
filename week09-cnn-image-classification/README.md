# Week 9 — Convolutional Neural Networks (CNN)

**Lecture theme:** CNN theory and real-world computer vision practice.

## Project: CNN Hands-On Lab — Classification, Transfer Learning, Object Detection

Pretrained CNNs are the backbone of practical computer vision. This week is a
three-part hands-on lab that goes from "use a pretrained model as-is" to
"adapt it to a new problem" to "find *where* objects are, not just what they
are":

1. **Image Classification** — load a pretrained **ResNet18** (ImageNet
   weights) and classify real photos into 1,000 categories, with no training
   at all.
2. **Transfer Learning** — adapt that same ResNet18 to a new problem it
   wasn't trained for (**Oxford-IIIT Pet**, 37 cat/dog breeds) by comparing
   **Feature Extraction** (freeze the backbone, train only a new output
   layer) against **Fine-tuning** (also unfreeze the last conv block, with a
   smaller learning rate).
3. **Object Detection** — use a pretrained **YOLO11n** to find *and locate*
   multiple objects in images and video, and see how confidence threshold
   and NMS (IoU threshold) change the results.

Each part only needs the shared setup in Part 0, so you can run Parts 1, 2,
and 3 in any order.

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week09-cnn-image-classification/project.ipynb)

A GPU runtime (`Runtime > Change runtime type`) is recommended but not
required — Part 2's training loop is just slower on CPU. The full notebook
takes roughly 10–15 minutes end-to-end on a Colab GPU.
