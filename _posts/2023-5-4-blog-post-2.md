---
title: 'The Reading of An Image is Worth 16X16 Words: Transformers for Image Recognition at Scale'
date: 2023-05-04
permalink: /posts/2023/05/blog-post-2
tags:
  - Transformer
  - Self-Attention
  - Vision
---

With the propose of the Transformer model, most NLP tasks have been provided with a standard solution framework, but its application in computer vision still faces great limitations. Most architectures adopt a mixed structure of CNN and Transformer to solve the problem. The introduction of ViT (Vision Transformer) achieves an approximation to the SOTA architecture with fewer computational resources.

## Overall Framwork of ViT

In the design process of the ViT architecture, the authors tried to make as few changes as possible to the original Transformer architecture, in order to achieve an out-of-the-box solution for computer vision problems.

![framwork](/images/2023/05/post2/pic0.png)

The standard Transformer receives as input a 1D sequence of token embeddings. To handle 2D images, we reshape the image $x\in R^{H×W×C}$ into a sequence of flattened 2D patches $x_p \in R^{N×(P^2·C)}$, where $(H, W)$ is the resolution of the original image, $C$ is the number of channels, $(P, P)$ is the resolution of each image patch, and $N = HW/P^2$ is the resulting number of patches, which also serves as the effective input sequence length for the Transformer. The Transformer uses constant latent vector size $D$ through all of its layers, so we flatten the patches and map to $D$ dimensions with a trainable linear projection. We refer to the output of this projection as the patch embeddings.

Inspired by the [class] token in BERT, the author added a learnable label at the beginning of the sequence, which is implemented by an MLP.The model also includes learnable 1D positional embeddings.

Finally, the transformer encoder consists of MSA, MLP, LN, and residual connection modules, and there are $L$ layers in total.

## Experiments
In this experiment, three different scales of ViT were designed and trained using the Adam optimization method.

First, the performance of three different ViT models compared to SOTA methods was evaluated on various datasets for three classification tasks. Second, the impact of training set size on model performance was investigated using two methods: training with different sized datasets and training with the same dataset at different scales. Finally, the effect of different training parameters and strategies on model performance, as well as the intrinsic behavior of the model during training, were also studied.

## Innovation
* Using self-attention mechanism instead of CNN: ViT uses self-attention mechanism to capture the relationships between input sequences, replacing the traditional application of convolutional neural networks (CNNs) in image processing. This method can provide better global information processing capabilities while reducing dependence on image-specific inductive biases.

* Sequence patching and position embeddings: ViT cuts the input image into a set of small image patches and uses learnable position embeddings to represent their positions in the input sequence. This method can provide better spatial information processing capabilities while reducing dependence on image-specific inductive biases.

* Multi-scale feature fusion: ViT uses a multi-scale feature fusion method to fuse feature blocks of different scales to improve the model's generalization and robustness.

* Fewer parameters: Compared to other advanced visual models such as ResNet and EfficientNet, ViT uses fewer parameters to achieve similar accuracy. This makes ViT still offer excellent performance in scenarios with limited computing resources.