# Breast Cancer Image Classification with Random Forest

## Description
Hybrid breast cancer histopathology classification using deep features from a pretrained ResNet18 and a Random Forest classifier. Achieves 85% accuracy and 0.91 ROC-AUC, with improved recall via threshold tuning for better cancer detection.

## Dataset
- **Dataset:** Breast Histopathology Images (IDC)  
- **Samples:** 277,524 image patches from 279 patients  
- **Image size:** 50×50 pixels  
- **Class imbalance:** More non-cancerous than cancerous samples  
- **Link:** [Breast Histopathology Images (IDC)](https://www.kaggle.com/datasets/paultimothymooney/breast-histopathology-images)

## Methodology
1. **Feature Extraction**  
   - Pretrained ResNet18 as a fixed feature extractor  
   - Classification head removed  
   - 512-dimensional feature vectors extracted  
   - No fine-tuning applied  

2. **Classification**  
   - Random Forest trained on extracted features  
   - 80/20 stratified train-test split  
   - Class weighting to address imbalance  

3. **Threshold Optimization**  
   - Default threshold (0.5): Precision 0.77, Recall 0.70, F1 0.73  
   - Tuned threshold (0.3): Precision 0.65, Recall 0.85, F1 0.74  

## Results
| Metric | Default (0.5) | Tuned (0.3) |
|--------|---------------|-------------|
| Accuracy | 85% | 85% |
| Precision (cancer) | 0.77 | 0.65 |
| Recall (cancer) | 0.70 | 0.85 |
| F1-score (cancer) | 0.73 | 0.74 |
| ROC-AUC | 0.91 | 0.91 |

## Key Contributions
- Combines pretrained CNN features with classical ML for histopathology classification  
- Effective Random Forest application on a large-scale dataset  
- Threshold tuning improves recall, critical for cancer detection  
- Scalable, interpretable, and computationally efficient

## Installation
```bash
git clone <repository_url>
cd breast-cancer-rf
pip install -r requirements.txt
