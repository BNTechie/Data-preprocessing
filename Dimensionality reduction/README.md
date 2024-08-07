# Dimensionality Reduction 
## What is dimensionality reduction?
Dimensionality reduction is a significant step in data analysis for high-dimensional data, where the number of features is reduced to simplify the model, lower computational cost, and remove issues like collinearity, overfitting, etc. The reduction techniques transform high-dimensional data into a lower-dimensional form (ideally, closest to its intrinsic dimension) while preserving as much information as possible. This is a popular technique in signal processing, neuroinformatics, bioinformatics,  and speech recognition, where one has to deal with a large number of observations and/or a large number of variables.

### Scenario: 
While working with real-life datasets, for example, in bioinformatics, we often encounter genomics datasets with hundreds of features each representing the gene's expression level. Analyzing such a high-dimensional dataset can be computationally expensive and due to the curse of dimensionality, it can be hard to draw any meaningful insights from it. Dimensionality reduction techniques can be powerful tools to adopt in such a situation. Data can be summarized in a few significant dimensions, making it easier to visualize and interpret. 

Let's discuss the key benefits of implementing this method.

### Key benefits of dimensionality reduction in data analysis

##### 1. Reduces Computational Complexity and speeds Up Learning Algorithms
High-dimensional data can be computationally expensive to process. Dimensionality reduction techniques simplify the data, reducing the computation needed for further analysis.
Many machine learning algorithms(e.g., Support Vector Machines, Linear regression models, Decision trees, Naive Bayes, etc) scale poorly with the number of features. The performances of these algorithms improve after the dimensionality reduction of large datasets. 

##### 2. Reduces the Curse of Dimensionality and improves model performance

As the number of dimensions increases, the volume of the space increases exponentially, making the data sparse. This sparsity is problematic for many algorithms that rely on dense data distributions. Dimensionality reduction reduces this effect.

High-dimensional data can lead to overfitting in machine learning models because the model can learn noise rather than the actual signal. Reducing the number of dimensions helps in creating
simpler models that generalize better to unseen data.

In high-dimensional data, features can be highly correlated (multicollinearity), which leads to poor model performance. Dimensionality reduction techniques can help remove these correlated features, leading to better model performance and interpretability.


##### 4. Enhances Visualization
 Dimensionality reduction techniques such as PCA, t-SNE, and UMAP enable us to project high-dimensional data into 2D or 3D space for visualization, making it easier to interpret as human intuition and perception are limited to 2D or 3D visualizations.


###### Example with the Iris Dataset

To illustrate these benefits, let's look at the Iris dataset. Without dimensionality reduction, it would be challenging to visualize how the three species are distributed in the feature space. Using techniques like PCA or t-SNE, we can project the data into a lower-dimensional space and visualize it: 
[Jupyter Notebook ](https://github.com/BhadraNivedita/Dimensionality-reduction-in-R-/blob/main/Dimensionality%20reduction%20in%20R.ipynb)
However, the iris dataset is not an idea example of a high-dimensional dataset. We will discuss this dataset for simplicity.


## Popular methods:

### Principal Component Analysis (PCA)

Principal Component Analysis (PCA) is a simple yet powerful technique for dimensionality reduction. It is a linear method that transforms the data into a set of orthogonal components, known as principal components, which capture the maximum variance in the data.

PCA involves the following key steps:

- **Standardizing the data**.
- **Computing the covariance matrix**
- **Finding eigenvalues and eigenvectors of the covariance matrix**
- **Selecting the top k principal components**
- **Transforming the original data into the new k-dimensional space**


### Linear Discriminant Analysis (LDA):

LDA, a supervised method, aims to find a linear combination of features that best separates two or more classes. It is specifically useful when the number of samples per class is limited.

LDA involves the following steps:

-**Assumptions**:
Data within each class is normally distributed and different classes have the same covariance matrix.
-**Aim**-
Maximize the ratio of between-class variance to the within-class variance in the dataset, thus ensuring maximal separability.

-**Mathematical steps**-
1. **Compute the Mean Vectors**
   - Compute the mean vectors for each class:
     \[
     \mathbf{m}_i = \frac{1}{N_i} \sum_{x \in \mathcal{D}_i} x
     \]
     where \( \mathbf{m}_i \) is the mean vector of class \( i \), \( N_i \) is the number of samples in class \( i \), and \( \mathcal{D}_i \) is the set of samples in class \( i \).

2. **Compute the Scatter Matrices**
   - Compute the within-class scatter matrix \( S_W \):
     \[
     S_W = \sum_{i=1}^k \sum_{x \in \mathcal{D}_i} (x - \mathbf{m}_i)(x - \mathbf{m}_i)^T
     \]
   - Compute the between-class scatter matrix \( S_B \):
     \[
     S_B = \sum_{i=1}^k N_i (\mathbf{m}_i - \mathbf{m})(\mathbf{m}_i - \mathbf{m})^T
     \]
     where \( \mathbf{m} \) is the overall mean vector of the entire dataset.

3. **Compute the Eigenvectors and Eigenvalues**
   - Solve the generalized eigenvalue problem for the matrix \( S_W^{-1} S_B \):
     \[
     S_W^{-1} S_B \mathbf{v} = \lambda \mathbf{v}
     \]
     where \( \lambda \) are the eigenvalues and \( \mathbf{v} \) are the eigenvectors.

4. **Select the Linear Discriminants**
   - Sort the eigenvectors by their corresponding eigenvalues in descending order.
   - Select the top \( k \) eigenvectors to form a transformation matrix \( W \).

5. **Transform the Data**
   - Project the data onto the new subspace:
     \[
     \mathbf{Y} = \mathbf{X} \mathbf{W}
     \]
     where \( \mathbf{Y} \) is the transformed dataset, \( \mathbf{X} \) is the original data matrix, and \( \mathbf{W} \) is the matrix of selected eigenvectors.






### t-Distributed Stochastic Neighbor Embedding (t-SNE):

t-SNE is a non-linear method for reducing the dimensionality of a dataset while preserving the local structure of the data.

### Uniform Manifold Approximation and Projection (UMAP):

UMAP is a non-linear method for dimensionality reduction that is particularly good at preserving the global structure of the data.

### Independent Component Analysis (ICA):

Independent Component Analysis (ICA) is used to separate a multivariate signal into additive, independent components.

### Factor Analysis (FA):

Factor Analysis (FA) is used to describe variability among observed, correlated variables in terms of potentially lower unobserved variables called factors.

 ### Multidimensional Scaling (MDS):

Multidimensional Scaling (MDS) is a means of visualizing the level of similarity of individual cases of a dataset.

