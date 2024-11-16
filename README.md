# Demo of Code-Switching Language Identification Mask Out

This is the demo and also proof of the concept

## File Structure

```
project_root/
├── CS_Dataset.py
├── train.py
├── loss.py
├── utils/
│   └── build_datasets.py
├── lid_hineng
│   ├── dev.conll
│   ├── test.conll
│   └── train.conll
├── lid_spaeng
│   ├── dev.conll
│   ├── test.conll
│   └── train.conll
├── lid_nepeng
│   ├── dev.conll
│   ├── test.conll
│   └── train.conll
├── logs
├── outputs
└── plot
```

`analysis.py` is for analyzing the information about the dataset, like number of classes and label distribution.

We are using [LinCE datasets](https://ritual.uh.edu/lince/datasets), which are `lid_hineng` and  `lid_spaeng` with train, dev and test datasets in .conll format.

## Train the model

```bash
python train.py
```

Train the model on the English-Spanish with masking out and test on the English-Hindi.

## Results
![Loss](plot/training_curves.png)

```txt
2024-11-16 01:05:20,318 [INFO] Starting training...
2024-11-16 01:06:26,931 [INFO] Epoch 1/10: Train Loss = 0.3164, Dev F1 Macro = 0.5031, Dev F1 Weighted = 0.5384
2024-11-16 01:06:27,561 [INFO] Saved new best model with F1 Macro: 0.5031
2024-11-16 01:07:33,014 [INFO] Epoch 2/10: Train Loss = 0.2168, Dev F1 Macro = 0.8429, Dev F1 Weighted = 0.8633
2024-11-16 01:07:33,559 [INFO] Saved new best model with F1 Macro: 0.8429
2024-11-16 01:08:38,946 [INFO] Epoch 3/10: Train Loss = 0.1143, Dev F1 Macro = 0.9125, Dev F1 Weighted = 0.9209
2024-11-16 01:08:39,336 [INFO] Saved new best model with F1 Macro: 0.9125
2024-11-16 01:09:44,720 [INFO] Epoch 4/10: Train Loss = 0.0844, Dev F1 Macro = 0.9335, Dev F1 Weighted = 0.9390
2024-11-16 01:09:45,030 [INFO] Saved new best model with F1 Macro: 0.9335
2024-11-16 01:10:50,621 [INFO] Epoch 5/10: Train Loss = 0.0715, Dev F1 Macro = 0.9467, Dev F1 Weighted = 0.9509
2024-11-16 01:10:50,925 [INFO] Saved new best model with F1 Macro: 0.9467
2024-11-16 01:11:56,530 [INFO] Epoch 6/10: Train Loss = 0.0634, Dev F1 Macro = 0.9567, Dev F1 Weighted = 0.9599
2024-11-16 01:11:56,841 [INFO] Saved new best model with F1 Macro: 0.9567
2024-11-16 01:13:02,514 [INFO] Epoch 7/10: Train Loss = 0.0583, Dev F1 Macro = 0.9616, Dev F1 Weighted = 0.9645
2024-11-16 01:13:02,842 [INFO] Saved new best model with F1 Macro: 0.9616
2024-11-16 01:14:08,399 [INFO] Epoch 8/10: Train Loss = 0.0551, Dev F1 Macro = 0.9672, Dev F1 Weighted = 0.9694
2024-11-16 01:14:08,710 [INFO] Saved new best model with F1 Macro: 0.9672
2024-11-16 01:15:14,278 [INFO] Epoch 9/10: Train Loss = 0.0520, Dev F1 Macro = 0.9668, Dev F1 Weighted = 0.9690
2024-11-16 01:16:19,521 [INFO] Epoch 10/10: Train Loss = 0.0498, Dev F1 Macro = 0.9694, Dev F1 Weighted = 0.9716
2024-11-16 01:16:19,845 [INFO] Saved new best model with F1 Macro: 0.9694
2024-11-16 01:16:19,846 [INFO] Evaluating on test set...
2024-11-16 01:16:21,065 [INFO] Test Results: F1 Macro = 0.7989, F1 Weighted = 0.7879
```

## Issue

### 1. Only calculated the weights depend on the training data.
![label_distribution](plot/label_distribution.png)

## Forward step

### 1. Add early step.

### 2. Implement the code for other metrics.

### 3. Implement the code on the test dataset after different models with different mask prob are trained and saved. Show the final results.

### 4. Any potential optimization.



