## Dataset
- **FER2013**: 48x48 grayscale face images, 7 emotions
- **Training**: 28,709 samples
- **Validation**: 3,589 samples

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
2. **Enable GPU**: Runtime → Change runtime type → GPU → Save
3. Run cells in this exact order:
   - Setup cell (imports all libraries)
   - WandB login 
   - Download dataset (upload kaggle.json when prompted)
   - Dataset class
   - Model architectures  
   - Training functions
   - Individual experiments (1, 2, 3, 4)
4. Each experiment automatically logs to WandB

## Important Notes
- **Dataset file**: Use `icml_face_data.csv` (not fer2013.csv)
- **Column names**: Have spaces (`' Usage'`, `' pixels'`)
- **WandB project**: `fer2013-cs231n`

## Files
- `fer2013_training.ipynb` - Main notebook with all experiments
- `README.md` - This file
- `requirements.txt` - Dependencies

## Actual Results (with GPU acceleration)
- **Experiment 1** (Simple CNN): **53.11%** - LeNet-style baseline
- **Experiment 2** (Small Filters): **54.81%** - Best performing! 3x3 filters more efficient  
- **Experiment 3** (Regularized): **54.44%** - Dropout + data augmentation
- **Experiment 4** (Batch Norm): **53.22%** - BatchNorm + regularization

## Why These Results?

**Small filters won** (54.81%) - This validates CS231n's teaching that multiple 3x3 filters are more efficient than single 5x5 filters. Your model learned better feature representations with less parameters.

**Modest improvements** - FER2013 is known to be a challenging dataset with label noise and quality issues. Even small improvements (1-2%) are meaningful progress.

**Regularization plateau** - Sometimes simpler models perform better when datasets are small or noisy. Your results show that over-regularization can hurt performance.

**Real research insight** - Not every technique improves every dataset! This is authentic machine learning research where you test hypotheses and learn from results.

## WandB Tracking
All experiments logged to: `fer2013-cs231n` project
- Real-time training curves
- Confusion matrices for each model
- Hyperparameter comparison
