# Semi-Supervised Denoising Diffusion Model for All-in-One Adverse Weather Removal

## Introduction
This is the official repository for our recent paper, "Semi-Supervised Denoising Diffusion Model for All-in-One Adverse Weather Removal", where more implementation details are presented.

## Abstract
Adverse weather removal aims to restore clear vision in adverse weather conditions. Despite the recent remarkable progress, existing methods are mostly tailored for specific weather types and rely heavily on large amounts of pairwise labeled data. Unlike previous arts, in this paper, we make the first attempt to propose a semi-supervised learning framework named SemiDDM-Weather, ingeniously integrating an accelerated Denoising Diffusion Model (DDM) into a standard teacher-student network, which achieves consistent visually highquality all-in-one adverse weather removal with limited labeled data. Specifically, to improve the accuracy of pseudo-labels for
semi-supervised learning, we construct a reliable bank to store the more scientifically defined “best-ever” outputs from the teacher network. Additionally, to harness the demonstrated generative strengths of diffusion models for inverse imaging tasks and to accelerate model inference—making diffusion models more suitable for our task—we adopt the fast Wavelet Diffusion model as the backbone, which requires only four, rather than hundreds, of sampling steps. More importantly, owing to the introduction of wavelet in our model, perceptually clearer vision can be restored, even surpassing the Ground Truth (GT). Experimental results validate that our approach, the first semi-supervised all-inone framework, outperforms fully supervised ones in restoration capability for various adverse weather scenarios.
<img src='overview.png'>
<p align="center">Figure 1. An overview of our approach.</p>

## Dependencies
- Ubuntu==18.04
- Pytorch==1.13.1
- CUDA==11.7

Other dependencies are listed in `requirements.txt`

## Usage

### 1. Prepare the dataset
We perform experiments for image deraining on [Snow100K](https://sites.google.com/view/yunfuliu/desnownet), combined image deraining and dehazing on [Outdoor-Rain](https://github.com/liruoteng/HeavyRainRemoval), and raindrop removal on
the [RainDrop](https://github.com/rui1996/DeRaindrop) datasets. 

### 2. Train
````bash
python tools/train.py --cfg configs/cityscapes/pidnet_small_cityscapes.yaml GPUS (0,1) TRAIN.BATCH_SIZE_PER_GPU 6
````

### 3. Test
````bash
python tools/train.py --cfg configs/cityscapes/pidnet_small_cityscapes.yaml GPUS (0,1) TRAIN.BATCH_SIZE_PER_GPU 6
````

## Acknowledgement
* The training code architecture is based on the [Semi-UIR](https://github.com/Huang-ShiRui/Semi-UIR) and [WaveDiff](https://github.com/VinAIResearch/WaveDiff)and thanks for their work.
* We also thank for the following repositories: [IQA-Pytorch](https://github.com/chaofengc/IQA-PyTorch)
* Thanks for their nice contribution.
