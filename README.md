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
2024-11-04 01:28:46,687 [INFO] Starting training...
2024-11-04 01:29:52,733 [INFO] Epoch 1/10: Train Loss = 0.0174, Dev F1 Macro = 0.2576, Dev F1 Weighted = 0.3516
2024-11-04 01:29:53,330 [INFO] Saved new best model with F1 Macro: 0.2576
2024-11-04 01:30:58,427 [INFO] Epoch 2/10: Train Loss = 0.0083, Dev F1 Macro = 0.3549, Dev F1 Weighted = 0.4159
2024-11-04 01:30:58,993 [INFO] Saved new best model with F1 Macro: 0.3549
2024-11-04 01:32:04,117 [INFO] Epoch 3/10: Train Loss = 0.0067, Dev F1 Macro = 0.3620, Dev F1 Weighted = 0.4205
2024-11-04 01:32:04,586 [INFO] Saved new best model with F1 Macro: 0.3620
2024-11-04 01:33:09,863 [INFO] Epoch 4/10: Train Loss = 0.0056, Dev F1 Macro = 0.3798, Dev F1 Weighted = 0.4258
2024-11-04 01:33:10,189 [INFO] Saved new best model with F1 Macro: 0.3798
2024-11-04 01:34:15,487 [INFO] Epoch 5/10: Train Loss = 0.0051, Dev F1 Macro = 0.3805, Dev F1 Weighted = 0.4301
2024-11-04 01:34:15,815 [INFO] Saved new best model with F1 Macro: 0.3805
2024-11-04 01:35:21,064 [INFO] Epoch 6/10: Train Loss = 0.0047, Dev F1 Macro = 0.4119, Dev F1 Weighted = 0.4607
2024-11-04 01:35:21,381 [INFO] Saved new best model with F1 Macro: 0.4119
2024-11-04 01:36:26,435 [INFO] Epoch 7/10: Train Loss = 0.0045, Dev F1 Macro = 0.4112, Dev F1 Weighted = 0.4664
2024-11-04 01:37:31,780 [INFO] Epoch 8/10: Train Loss = 0.0045, Dev F1 Macro = 0.4306, Dev F1 Weighted = 0.4705
2024-11-04 01:37:32,170 [INFO] Saved new best model with F1 Macro: 0.4306
2024-11-04 01:38:37,537 [INFO] Epoch 9/10: Train Loss = 0.0042, Dev F1 Macro = 0.4346, Dev F1 Weighted = 0.4748
2024-11-04 01:38:37,855 [INFO] Saved new best model with F1 Macro: 0.4346
2024-11-04 01:39:42,978 [INFO] Epoch 10/10: Train Loss = 0.0040, Dev F1 Macro = 0.4359, Dev F1 Weighted = 0.4761
2024-11-04 01:39:43,314 [INFO] Saved new best model with F1 Macro: 0.4359
2024-11-04 01:39:43,314 [INFO] Evaluating on test set...
2024-11-04 01:39:44,056 [INFO] Test Results: F1 Macro = 0.3022, F1 Weighted = 0.4259

```

## Issue

### 1. The distribution of labels is not balance.
![label_distribution](plot/label_distribution.png)

### 2. F1 score is so low!!!



