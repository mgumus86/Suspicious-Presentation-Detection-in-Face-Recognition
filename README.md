# Suspicious Presentation Detection in Face Recognition (Georgia Tech - CDA Project)

This project addresses the problem of biometric spoofing, where attackers attempt to fool face recognition systems using printed images or replayed videos. 
We used the **OULU-NPU dataset** and applied both classical machine learning algorithms and **convolutional neural networks (CNNs)** to detect such presentation attacks.

## Dataset

- **Source:** [OULU-NPU Dataset](http://www.ee.oulu.fi/research/ouspg/OULU-NPU/)
- **Total Videos:** 4,950 (990 genuine, 3,960 non-genuine)
- **Used Data:** Extracted and preprocessed face images
- **Image Size:** Cropped to 150x150 pixels
- **Attack Types:**
  - Printed photo (two variants)
  - Video replay (two variants)

## Methodology

Two major approaches:

### 1. Traditional ML + Feature Engineering
- Extracted 18 image distortion metrics (MSE, PSNR, SSIM, etc.)
- Trained:
  - Logistic Regression
  - SVM
  - KNN
  - Random Forest
  - AdaBoost (best performer among classical models)
- Used cross-validation and ROC/AUC for evaluation

### 2. Convolutional Neural Network (CNN)
- Input: raw face images (150x150)
- Architecture: 4 Conv2D blocks + max pooling + dropout + dense layers
- Trained using:
  - Data augmentation (flip, rotate, zoom)
  - Binary cross-entropy loss
  - ADAM optimizer
 
## Results

| Model           | ROC AUC | Accuracy |
|----------------|---------|----------|
| AdaBoost        | 0.796   | 72.6%    |
| CNN             | 0.926   | 83.9%    |

- CNN outperformed AdaBoost in overall accuracy and ROC-AUC.
- AdaBoost had higher recall for the "attack" class in some cases, suggesting possible trade-offs depending on application sensitivity.

## Project Structure
- `CNN.ipynb`: Core deep learning model
- `pull-images.ipynb`: Image acquisition
- `push-images.ipynb`: Preprocessing pipeline
- `imagepro/`: Image storage
- `requirements.txt`: Package dependencies

## Requirements

This project requires Python 3.8 to run the project notebooks. 

Specific python packages are also required and can be installed using the below command:
```
pip install -r requirements.txt
```

## Contributors

```markdown
## Contributors

- Mehmet Gumus — Model development & CNN implementation  
- Jacob Lee — Feature engineering & EDA  
- Matthew Mitchell — ML pipelines & tuning  


