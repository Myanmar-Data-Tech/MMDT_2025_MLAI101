## 1. Differences between SVM kernels
### Linear Kernel
The linear kernel creates a straight hyperplane decision boundary in the original feature space. The kernel computes the dot product between vectors without any transformation, making it the simplest kernel function.

### Polynomial Kernel
The polynomial kernel maps data into higher-dimensional space using polynomial combinations of features. With degree 3, this kernel captures complex, non-linear relationships.

### RBF (Radial Basis Function) Kernel
The RBF kernel creates circular/spherical decision boundaries by measuring similarity through Gaussian functions, allows creating for highly flexible, non-linear decision boundaries.

## 2. When to Use Each Kernel
- I would use Linear Kernel for high-dimensional datasets where the number of features exceeds the number of samples.
- Polynomial Kernel is better for the tasks which require interaction between pixel features (Eg. computer vision tasks). It is also suitable for medium-sized datasets with known polynomial relationships.
- RBF Kernel is suitable for complex pattern recognition tasks with unknown data distributions and non-linear problems with no prior knowledge of data structure.