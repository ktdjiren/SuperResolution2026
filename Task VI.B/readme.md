# Super-Resolution of Limited Dataset

## Project Overview
This project focuses on training a deep learning-based super-resolution algorithm to enhance low-resolution strong lensing images using a limited dataset of real HR/LR pairs collected from HSC and HST telescopes. The model is implemented using **PyTorch/Keras**, incorporating advanced training strategies such as augmentation, custom losses, and optimization techniques to achieve high accuracy.

### Dataset Description
The dataset consists of simulated strong lensing images with different resolutions:
- **High-Resolution (HR) images** (Ground truth images)
- **Low-Resolution (LR) images** (Degraded versions of HR images)

Dataset sample: ![Dataset Sample](https://github.com/ktdjiren/--SuperResolution/blob/main/Task%20III.B/sample_images%20.png)

---

## Implemented Model
To tackle this problem, I implemented and trained a **Custom Diffusion Autoencoder Model** with the following features:
- **Heavy Augmentation:** Improves generalization on limited datasets.
- **Custom Loss Functions:** Designed to optimize both pixel-wise and perceptual similarities.
- **AdamW Optimizer:** Used for stable training with weight decay.
- **Learning Rate Scheduler:** Adjusts learning rate dynamically to prevent overfitting.
- **Low Learning Rate:** Ensures fine-grained optimization for better convergence.
forward_diffusion_process: ![Dataset Sample](https://github.com/ktdjiren/--SuperResolution/blob/main/Task%20III.B/forward_diffusion_process.png)
---

## Model Performance Comparison
Below is a comparison between the basic **RCNN** model and my **Custom Diffusion Autoencoder Model**, evaluated based on accuracy metrics:

| Model                                | PSNR (dB) | SSIM  | MSE   |
|--------------------------------------|-----------|-------|-------|
| Residual Convolutional Neural Network (RCNN) | 26.02  | 0.5905 | 0.002924 |
| Custom Diffusion Autoencoder Model   | 28.75791976  | 0.68899942 | 0.00190619 |

output sample: ![Dataset Sample](https://github.com/ktdjiren/--SuperResolution/blob/main/Task%20III.B/Screenshot%202025-03-28%20030317.png)

---

## Implementation Details
This project is implemented using **PyTorch/Keras**, and the model is trained and evaluated as follows:

### Steps to Run the Code
1. Clone this repository:
   ```bash
   git clone https://github.com/ktdjiren/--SuperResolution.git
   ```

---

## Discussion
- **RCNN Model:** A basic deep learning approach that applies convolutional layers to improve resolution.
- **Custom Diffusion Autoencoder Model:** Achieves superior results due to its enhanced feature extraction and generative capabilities.

---

## Contact
For any queries or contributions, feel free to reach out:
📧 Email: [rawatamanamanaman1234@gmail.com]  
🔗 GitHub: [https://github.com/ktdjiren]

