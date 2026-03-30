# Multi-Class Classification for Strong Lensing Images

## Overview
This project builds a multi-class classification model to classify strong lensing images into three categories:
- **No substructure (no)**
- **Subhalo substructure (sphere)**
- **Vortex substructure (vort)**
## Sample Image
![sample_image](https://github.com/ktdjiren/--SuperResolution/blob/main/Common%20Test%20I.%20Multi-Class%20Classification/sample.png)

## Dataset & Approach
- **Dataset**: Images are min-max normalized. Additional normalization and **data augmentation** (rotation, flipping, brightness) can enhance performance.
- **Model**: A **CNN-based classifier** trained with **Adam optimizer** and **cross-entropy loss**.
- **Evaluation**: Metrics include **confusion matrix** and **ROC-AUC score**.

## Results
### Confusion Matrix
![Confusion Matrix](https://github.com/ktdjiren/--SuperResolution/blob/main/Common%20Test%20I.%20Multi-Class%20Classification/confusion_Marix.png)

### ROC Curve
![ROC Curve](https://github.com/ktdjiren/--SuperResolution/blob/main/Common%20Test%20I.%20Multi-Class%20Classification/ROC_curve.png)

AUC Scores:
- **No substructure**: 0.99
- **Subhalo substructure**: 0.96
- **Vortex substructure**: 0.99

##  How to Run the Code
Clone this repository:
```bash
   git clone https://github.com/ktdjiren/--SuperResolution.git
```


## Conclusion
This CNN model effectively classifies strong lensing images, with high performance on **no** and **vortex** classes. Future improvements may include **fine-tuning** and **transformer-based models**.

