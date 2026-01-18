# CHANGELOG

## 2026-01-18 00:46:53

### Completed
- Completed findings summary for Model 4 (Binary Classification) in Cell 63:
  - Documented test accuracy: 99.21%
  - Summarized key findings: binary classification easier than multi-class, class imbalance considerations, appropriate loss function selection

## 2026-01-18 00:45:10

### Completed
- Completed Model 4 (Binary Classification) implementation in Cell 55:
  - Implemented `BinaryNN` class with architecture: 784 -> 512 (ReLU) -> 1
  - Output is single logit (no sigmoid, as BCEWithLogitsLoss applies it internally)
  - Added `.squeeze(-1)` to match target tensor shape
  - Set criterion to `nn.BCEWithLogitsLoss()` for binary classification
  - Same optimizer (RMSprop, lr=0.001)

## 2026-01-18 00:27:00

### Completed
- Completed findings summary in Cell 45 for Models 1-3:
  - Documented test accuracy comparison: Model 1 (92.77%), Model 2 (97.97%), Model 3 (98.09%)
  - Summarized key findings on hidden layers, early stopping, and overfitting prevention

## 2026-01-18 00:22:52

### Completed
- Completed Model 3 training with early stopping in Cell 42:
  - Set `early_stop_patience=2` to stop training if val_loss doesn't improve for 2 consecutive epochs
  - Fixed parameter name from `patience` to `early_stop_patience` to match `train_model` function signature

## 2026-01-18 00:21:47

### Completed
- Completed Model 3 setup in Cell 40 (TwoLayerNN with early stopping):
  - Created new `TwoLayerNN` instance (same architecture as Model 2: 784 -> 512 -> 10)
  - Same optimizer (RMSprop, lr=0.001), criterion (CrossEntropyLoss), and metric_fn

## 2026-01-18 00:18:30

### Completed
- Completed prediction code in Cell 36:
  - Added `y_pred = predict_proba(model, X_test).argmax(axis=1)` to get predicted class labels

## 2026-01-18 00:17:20

### Completed
- Completed Model 2 (Two-layer fully-connected NN) implementation in Cell 28:
  - Implemented `TwoLayerNN` class with architecture: 784 -> 512 (ReLU) -> 10
  - Hidden layer with 512 units and ReLU activation
  - Output layer produces raw logits for CrossEntropyLoss
  - Same optimizer (RMSprop, lr=0.001), criterion (CrossEntropyLoss), and metric_fn as Model 1

## 2026-01-17 23:48:04

### Fixed
- Fixed `model_summary` function in Cell 15:
  - Added `import sys` and `sys.stdout.flush()` to ensure output is properly flushed in Colab/Jupyter
- Fixed typo in Cell 29: changed `model.summary(model)` to `model_summary(model)`

## 2026-01-17 23:29:28

### Completed
- Completed Model 1 (Perceptron/Multinomial Logistic Regression) implementation in Cell 16:
  - Implemented `Perceptron` class with single linear layer (784 -> 10)
  - Added conversion of one-hot labels to class indices (`y_train_idx`, `y_val_idx`, `y_test_idx`) using `argmax(axis=1)`
  - Created data loaders with batch_size=128 using `make_loaders` helper
  - Set criterion to `nn.CrossEntropyLoss()` for multi-class classification
  - Set optimizer to `torch.optim.RMSprop` with lr=0.001
  - Defined accuracy metric function to count correct predictions
