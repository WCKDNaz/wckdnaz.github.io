---
layout: default
---
# Machine Learning Projects
On this page, I will be uploading some machine learning projects that go through the process of loading data into a dataframe, inspecting the dataframe objects and attributes.
Simply put, it will be summarizing my workflow methods of using different libraries such as `sklearn`, `numpy`, `pyspark`, and `matplotlib` for demonstrating my own point of view
on how you can analyze, build, and eventually train a model. Confusion matrices will be used for means of measure, accordingly other measures of performances will be employed regarding
the project's nature.

## KNN MultiClass Classification - Supervised ML
This is a fairly simple project, utilizing `Sci-kit-learn's` KNN classifier in a nested `for` loop to iterate through 
different `N-Neighbors` and different `train/test` subsetting. Label columns was `Diabetes` and had values of either `0`, `1`, or `2` thus indicating whether a 
patient was `No-Diabetes`, `Type 1 Diabetic`, or `Type 2 Diabetic`. The dataset was clean, and had no null-values so no pre-processing was done in this one.
<br>

[Rendered Code Notebook](assets/machine-learning-assets/simple-knn-mcc.html) |
[Dataset CSV File](assets/machine-learning-assets/diabetes.csv) |
[Code Notebook](./knn-multiclass.md)
