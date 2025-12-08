# w207-predictive-maintenance 
## Deep Neural Network Multilabel Classification

### Existing Literature: Random Forest (Dereci & Tuzkaya, 2024)

Table adapted from Dereci & Tuzkaya (2024), Table 6.  

| Class          | Precision | Recall | F1-score | Support |
|----------------|-----------|--------|----------|---------|
| 0 (non-failure) | 0.99      | 0.99   | 0.99     | 1932    |
| 1 (failure)     | 0.76      | 0.62   | 0.68     | 68      |
| **Accuracy**    |           |        | **0.98** | **2000** |
| **Macro Avg.**  | 0.88      | 0.81   | 0.84     | 2000    |
| **Weighted Avg.** | 0.98    | 0.98   | 0.98     | 2000    |

**Reference**

Dereci, U., & Tuzkaya, G. (2024). *An explainable artificial intelligence model for predictive maintenance and spare parts optimization.* Supply Chain Analytics, 8, 100078. https://doi.org/10.1016/j.sca.2024.100078

We use this Random Forest model as a published benchmark for failure prediction performance.
Our multi-label deep neural network results (below) are reported on the same dataset, with tuned decision thresholds per label.


## Inference Performance (Tuned Thresholds)

| Label             | Precision | Recall | F1-Score | Support |
|-------------------|-----------|--------|----------|----------|
| TWF               | 0.92      | 0.98   | 0.95     | 120      |
| HDF               | 0.95      | 1.00   | 0.98     | 120      |
| PWF               | 1.00      | 0.93   | 0.97     | 120      |
| OSF               | 0.98      | 0.99   | 0.99     | 120      |
| RNF               | 0.95      | 1.00   | 0.98     | 120      |
| joint_PWF_OSF     | 1.00      | 1.00   | 1.00     | 120      |
| joint_TWF_RNF     | 0.99      | 1.00   | 1.00     | 120      |
| joint_HDF_PWF     | 1.00      | 1.00   | 1.00     | 120      |
| joint_HDF_OSF     | 1.00      | 1.00   | 1.00     | 200      |
| joint_TWF_OSF     | 1.00      | 1.00   | 1.00     | 200      |
| joint_TWF_PWF_OSF | 1.00      | 1.00   | 1.00     | 200      |

| Metric       | Precision | Recall | F1-Score | Support |
|---------------|-----------|--------|----------|----------|
| micro avg     | 0.98      | 0.99   | 0.99     | 1560     |
| macro avg     | 0.98      | 0.99   | 0.99     | 1560     |
| weighted avg  | 0.98      | 0.99   | 0.99     | 1560     |
| samples avg   | 0.77      | 0.77   | 0.77     | 1560     |


![Loss gradient for Binary Focal Loss](loss-gradient-fl-cd.png)


The best model was selected by maximizing Macro F1 on the validation set. The tuned-threshold performance by label is summarized below.

## Detailed Label Metrics (Tuned Thresholds)- Validation set

| Label   | Prevalence | Precision @tuned | Recall @tuned | F1 @tuned | PR_AUC  | ROC_AUC | TP   | FP  | FN  | TN    | max_F1_OOF |
|----------|-------------|------------------|----------------|------------|----------|----------|------|-----|-----|-------|-------------|
| **HDF** | 0.059701 | 0.956232 | 0.930556 | 0.943219 | 0.976325 | 0.998721 | 1005 | 46 | 75 | 16964 | 0.950805 |
| **OSF** | 0.059701 | 0.988706 | 0.891667 | 0.937683 | 0.982070 | 0.998316 | 963 | 11 | 117 | 16999 | 0.948027 |
| **PWF** | 0.059701 | 0.973048 | 0.969444 | 0.971243 | 0.994739 | 0.999700 | 1047 | 29 | 33 | 16981 | 0.973588 |
| **RNF** | 0.059701 | 0.920276 | 0.865741 | 0.892176 | 0.969027 | 0.997898 | 935 | 81 | 145 | 16929 | 0.910862 |
| **TWF** | 0.059701 | 0.900552 | 0.905556 | 0.903047 | 0.911857 | 0.996875 | 978 | 108 | 102 | 16902 | 0.911392 |

---

## Joint Label Metrics

| Label        | Prevalence | Precision @tuned | Recall @tuned | F1 @tuned | PR_AUC  | ROC_AUC | TP   | FP  | FN  | TN    | max_F1_OOF |
|---------------|-------------|------------------|----------------|------------|----------|----------|------|-----|-----|-------|-------------|
| **HDF_PWF**   | 0.059701 | 0.989918 | 1.000000 | 0.994933 | 0.998956 | 0.999936 | 1080 | 11 | 0 | 16999 | 0.996310 |
| **PWF_OSF**   | 0.059701 | 0.987940 | 0.910185 | 0.947470 | 0.998276 | 0.999894 | 983 | 12 | 97 | 16998 | 0.987654 |
| **TWF_RNF**   | 0.059701 | 0.978261 | 1.000000 | 0.989011 | 0.996061 | 0.999824 | 1080 | 24 | 0 | 16986 | 0.994933 |
| **HDF_OSF**   | 0.099502 | 0.999445 | 1.000000 | 0.999722 | 0.999878 | 0.999988 | 1800 | 1 | 0 | 16289 | 0.999722 |
| **TWF_OSF**   | 0.099502 | 0.998899 | 1.000000 | 0.999445 | 0.999883 | 0.999988 | 1800 | 2 | 0 | 16288 | 0.999722 |
| **TWF_PWF_OSF** | 0.099502 | 0.944386 | 1.000000 | 0.971398 | 1.000000 | 1.000000 | 1800 | 106 | 0 | 16184 | 1.000000 |

