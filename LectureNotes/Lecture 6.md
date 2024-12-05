```
Assignment 1: Released
Deadline: 1st September 2024
```
## Name: Harsh Sanjay Roniyar

### Roll Number: 22B3942
### Regularization
Penalizing overfitting to the training data curve, in some sense constraining the model to reduce the complexity of the model.

Loss Function on including the **L2 Norm** for regularization becomes - $$L = L_{\text{old }} + \lambda\sum_{i=1}^{N} w_i^2 $$
**Note** that regularization hurts training set performance! This is because it limits the ability of the network to overfit to the training set. But since it ultimately gives better test accuracy, it is helping your system

### Performance Metric
A judge for the model
### Data Preparation
1. **Train** - Learn (optimize parameters)
2. **Validation** - Compare hyperparameters
3. **Test** - One final model evaluation

Having more data-points reduce chances of overfitting and thus less variance.
### K-Fold Cross Validation
1. Train K times on K-1 folds and each time validate on the hold-out fold.
2. Select hyperparameters
3. Train on all K folds using the selected hyperparameters (can use Train + Validation data together).
Thus, validation is done and now final test can be done using the test data.


