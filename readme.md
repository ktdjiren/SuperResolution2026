# Enhancing Astronomical Strong Lensing Images Using Diffusion Models: A Deep Learning Approach

## Introduction

In the realm of modern astrophysics, high-resolution imaging plays a pivotal role. One particular area of interest is **strong gravitational lensing**, a cosmic phenomenon where the light from a distant galaxy is bent around a massive object, like a galaxy cluster, creating arcs and distorted images of the background object. These distorted arcs are more than visual oddities; they are critical to understanding dark matter distributions, verifying cosmological models, and probing the expansion of the universe.

Despite their significance, most strong lensing observations are captured at relatively low resolutions due to limitations in telescope optics, atmospheric distortions, or instrument design. Telescopes such as the **Hyper Suprime-Cam (HSC)** and the **Hubble Space Telescope (HST)** provide valuable data, but often in formats that are noisy or undersampled. Enhancing these images is a crucial step toward extracting accurate scientific insights.

This project aims to address this challenge using a cutting-edge solution: **diffusion-based super-resolution modeling**. By leveraging the power of generative modeling, particularly **Denoising Diffusion Probabilistic Models (DDPM)**, we demonstrate a novel approach to reconstructing high-resolution versions of low-resolution lensing data.

## Problem Statement

The inherent difficulties in enhancing strong lensing images are threefold:

* **Data scarcity**: High-quality lensing images are limited, which restricts supervised training.
* **Noisy inputs**: Real astronomical data is often corrupted by instrumental noise and atmospheric interference.
* **Loss of fine features**: Many super-resolution techniques produce visually clean images but fail to preserve subtle arc structures.

To address these, our goal is to design a model that not only enhances image resolution but does so in a way that **preserves scientific fidelity**.
![Sample Image](https://github.com/ktdjiren/--SuperResolution/blob/main/sample_images.png)


## Previous Approaches

Traditional super-resolution approaches rely on interpolation methods (bicubic, bilinear), which often blur the unique features of lensing arcs. More recently, CNN-based models such as **SRCNN** and **RCAN** have been introduced. While these perform better in general settings, they still struggle with:

* Limited robustness to noise
* Generalization with small datasets
* Inability to reproduce sharp curvature features seen in lensing arcs

## Our Approach: Diffusion-Based Autoencoder for Super-Resolution

### Architecture Overview

Our method introduces a custom **diffusion autoencoder** consisting of:

* **Encoder**: A deep convolutional network that compresses the input image to a latent representation.
* **Noise Conditioning**: The latent is perturbed through controlled Gaussian noise, inspired by DDPM.
* **Decoder**: A symmetrical network that reconstructs the image by reversing the noise process step-by-step.

This model is trained using a combination of **pixel-wise reconstruction losses** and **feature-space losses** that emphasize perceptual quality and structural consistency.

### Key Innovations

1. **GAN-based augmentation**: We used a Generative Adversarial Network to augment the dataset by generating synthetic variations of lensing arcs, improving generalization.
2. **Hybrid Loss Function**: Our custom loss includes:

   * Mean Squared Error (MSE)
   * Structural Similarity Index (SSIM)
   * Perceptual Loss via VGG features
3. **Dynamic Noise Scheduling**: Instead of static noise levels in diffusion, we tested dynamic schedules depending on the input’s noise profile.

## Experimental Setup

* **Dataset**: Simulated HSC-like lensing images with paired low-resolution and high-resolution versions.
* **Training Configuration**:

  * Epochs: 120
  * Batch Size: 16
  * Optimizer: AdamW with cosine LR scheduling
* **Evaluation Metrics**:

  * PSNR (Peak Signal-to-Noise Ratio)
  * SSIM (Structural Similarity Index)
  * Visual inspection for arc integrity and sharpness

## Results

<table style="width:100%; table-layout:fixed">
  <thead>
    <tr>
      <th style="text-align:left; width:33%">Model</th>
      <th style="text-align:center; width:33%">PSNR (dB)</th>
      <th style="text-align:right; width:33%">SSIM</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>SRCNN</td>
      <td style="text-align:center">37.80</td>
      <td style="text-align:right">0.912</td>
    </tr>
    <tr>
      <td>RCAN</td>
      <td style="text-align:center">39.56</td>
      <td style="text-align:right">0.948</td>
    </tr>
    <tr>
      <td><strong>Ours</strong></td>
      <td style="text-align:center"><strong>42.11</strong></td>
      <td style="text-align:right"><strong>0.977</strong></td>
    </tr>
  </tbody>
</table>

Our model outperforms both SRCNN and RCAN, particularly in edge preservation and brightness reconstruction. Visual inspection confirms that arc features are better maintained, and background noise is effectively suppressed.

## Discussion

The diffusion-based approach offers significant advantages in scientific imaging:

* **Noise robustness**: The denoising nature of DDPM enables the model to handle real-world astronomical noise better than deterministic CNNs.
* **High-detail recovery**: Subtle details, such as faint arcs or secondary lensing effects, are preserved more effectively.
* **Generalization**: Due to noise conditioning and GAN-based augmentation, the model performs well on unseen lensing structures.

These qualities make diffusion models not just a viable alternative but a **superior candidate** for astrophysical image enhancement.

## Applications Beyond Astronomy

The framework is applicable to multiple domains:

* **Medical imaging**: CT/MRI scans enhancement
* **Remote sensing**: Satellite image sharpening
* **Microscopy**: Cellular structure reconstruction

## Future Directions

* Test with **real HST and Euclid datasets**
* Add **multi-modal conditioning** using metadata like redshift or filter band
* Explore **cross-modality models** combining image + spectral inputs
* Real-time inference pipeline using ONNX or TensorRT

## Author

**Aman Rawat**
* AI-ML Intern, Grull Technologies Pvt Ltd
* B.Tech Final Year, IIT (ISM) Dhanbad
* GitHub: [ktdjiren](https://github.com/ktdjiren)
* LinkedIn: [aman-rawat](https://www.linkedin.com/in/aman-rawat-08556b272)
* Email: [rawatamanamanaman1234@gmail.com](mailto:rawatamanamanaman1234@gmail.com)


## References

* Dong et al., "Image Super-Resolution Using Deep Convolutional Networks" (SRCNN)
* Zhang et al., "Image Super-Resolution Using Very Deep Residual Channel Attention Networks" (RCAN)
* Ho et al., "Denoising Diffusion Probabilistic Models" (DDPM)
* Simonyan et al., "Very Deep Convolutional Networks for Large-Scale Image Recognition" (VGG)


