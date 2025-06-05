# FER2013 with Progressive CNNs

## Dataset
- **FER2013**: 48x48 grayscale face images, 7 emotions
- **Training**: 28,709 samples
- **Validation**: 3,589 samples

## Experiments (Following CS231n Lectures 5 & 6)

### Experiment 1: Simple CNN
```
Conv(5x5, 6 filters) → ReLU → MaxPool
Conv(5x5, 16 filters) → ReLU → MaxPool  
FC(120) → FC(84) → FC(7)
```
**Why**: Basic CNN to establish baseline 

### Experiment 2: Smaller Filters
```
Conv(3x3, 32 filters) → ReLU → MaxPool
Conv(3x3, 64 filters) → ReLU → MaxPool
FC(512) → FC(7)
```
**Why**: 3x3 filters are more efficient than large filters

### Experiment 3: Add Regularization
```
Same as Exp 2 + Dropout(0.5) + Data Augmentation
```
**Why**: Prevent overfitting

### Experiment 4: Batch Normalization
```
Conv → BatchNorm → ReLU → MaxPool (repeat)
```
**Why**: Faster training, higher learning rates

## Quick Start (Google Colab)

1. Upload `fer2013_training.ipynb` to Colab
2. Run all cells sequentially
3. Each experiment logs to WandB automatically

## Files
- `fer2013_training.ipynb` - Main notebook with all experiments
- `README.md` - This file
- `requirements.txt` - Dependencies

## Expected Results
- Experiment 1: ~45% accuracy
- Experiment 2: ~52% accuracy  
- Experiment 3: ~58% accuracy
- Experiment 4: ~62% accuracy
