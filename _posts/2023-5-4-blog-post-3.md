---
title: 'The Reading of Swin Transformer: Hierarchical Vision Transformer using Shifted Windows'
date: 2023-05-04
permalink: /posts/2023/05/blog-post-3
tags:
  - Transformer
  - Shifted Window
  - Vision
---

This paper introduces a new form of vision Transformer, called Swin Transformer, which uses shifted windows to process higher resolution images. Compared to previous ViT models, which have a quadratic growth in processing time with respect to image size, the Swin Transformer achieves linear growth with the use of shifted windows.

## Overall Architecture


![framework](/images/2023/05/post3/pic0.png)

An overview of the Swin Transformer architecture is presented, which illustrates the tiny version (Swin-T). It first splits an input RGB image into non-overlapping patches by a patch splitting module, like ViT. Each patch is treated as a “token” and its feature is set as a concatenation of the raw pixel RGB values. In our implementation, we use a patch size of $4 × 4$ and thus the feature dimension of each patch is $4 × 4 × 3 = 48$. A linear embedding layer is applied on this raw-valued feature to project it to an arbitrary dimension (denoted as $C$).

Several Transformer blocks with modified self-attention computation (Swin Transformer blocks) are applied on these patch tokens. The Transformer blocks maintain the number of tokens ($\frac H 4 × \frac W 4$), and together with the linear embedding are referred to as “Stage 1”.

After that, the input is merged using patch merging layers, passed through Swin Transformer Blocks, and finally output($\frac H 8 × \frac W 8 × 2C$).

The Swin Transformer model processes the input image through multiple stages of Swin Transformer Blocks and patch merging operations, gradually reducing the resolution of the feature maps and extracting higher-level representations. Finally, the model outputs a feature map that is similar to what a CNN architecture would output. This feature map can be used for various downstream tasks such as image classification, object detection, and segmentation.

## Innovation & Technical Details

* A Swin Transformer block consists of a shifted window based MSA module, followed by a 2-layer MLP with GELU non-linearity in between. A LayerNorm (LN) layer is applied before each MSA module and each MLP, and a residual connection is applied after each module.
* Proposes the use of shifted windows for image segmentation, which achieves linear growth in processing time with increasing image size. The shifted windows method involves sliding the window in a shifted manner to avoid redundant computations and handle image regions with different sizes. With this technique, the processing time grows linearly with the size of the image, which is a significant improvement over traditional methods that have a quadratic growth in processing time.
* This paper proposes an efficient batch processing method called cycle-shifting, which addresses the issue of increased computational complexity due to padding by cyclically shifting the window towards the upper-left direction. With this approach, the number of batched windows remains the same as that of regular window partitioning, and thus is also efficient.

## Experiment
Before conducting experiments, the authors divided the Swin-T model into four different parameter configurations. They then evaluated the performance of the model on various computer vision tasks, including ImageNet-1K, COCO, and ADE20K, and compared the impact of different training datasets as well as the performance gap with SOTA methods. Ablation studies were also performed to investigate the effects of various factors such as relative position bias and different self-attention methods on model performance.