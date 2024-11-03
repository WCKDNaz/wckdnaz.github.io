---
layout: default
---
# Machine Learning Projects
On this page, I will be uploading some machine learning projects that go through the process of loading data into a dataframe, inspecting the dataframe objects and attributes.
Simply put, it will be summarizing my workflow methods of using different libraries such as `sklearn`, `numpy`, `pyspark`, and `matplotlib` for demonstrating my own point of view
on how you can analyze, build, and eventually train a model. Confusion matrices will be used for means of measure, accordingly other measures of performances will be employed regarding
the project's nature.

## KNN MultiClass Classification - Supervised ML
<details>
  <summary>Details and Code</summary>
  <br>
  
  This is a fairly simple project, utilizing `Sci-kit-learn's` KNN classifier in a nested `for` loop to iterate through 
  different `N-Neighbors` and different `train/test` subsetting. Label columns was `Diabetes` and had values of either `0`, `1`, or `2` thus indicating whether a 
  patient was `No-Diabetes`, `Type 1 Diabetic`, or `Type 2 Diabetic`. The dataset was clean, and had no null-values so no pre-processing was done in this one.
  
  <br>
  
  [Rendered Code Notebook]()
  
  <br>
  
  [Download Dataset CSV File]()
  
  <br>
  
  ```python
  # Initializing libraries code block
  import seaborn as sns
  import pandas
  import matplotlib.pyplot as plt
  from sklearn.model_selection import train_test_split
  from sklearn.preprocessing import StandardScaler
  from sklearn.metrics import accuracy_score, confusion_matrix
  from sklearn.neighbors import KNeighborsClassifier

  # Initializing dataset from drive
  data_diabetes = pandas.read_csv('/content/drive/MyDrive/ML&Big_Data/diabetes.csv')
  
  # Describing dataframe objects, gathering info such as mean, std deviation,
  # what percentage are in the different quartiles, and maximum values a single object can hold
  data_diabetes.describe()
  data_diabetes.info()
  
  # Describing dataframe array 'Diabetes'
  data_diabetes['Diabetes'].unique()
  
  # Feature scaling code block
  unscaled_features = data_diabetes.drop(columns=['Diabetes'])
  label = data_diabetes['Diabetes']
  scaler_metric = StandardScaler()
  scaled_features = scaler_metric.fit_transform(unscaled_features)
  scaled_features.view()
  
  # Initial Training
  test_vals = [0.15, 0.2, 0.25, 0.3,]
  neighbor_values = [2, 5, 7, 10]
  for value in test_vals:
    features_tr, features_te, labels_tr, labels_te = train_test_split(scaled_features, label, test_size=value, random_state=42)
    for iteration in neighbor_values:
      knnmodel = KNeighborsClassifier(n_neighbors=iteration)
      knnmodel.fit(features_tr, labels_tr)
      pred = knnmodel.predict(features_te)
  
      pred_accuracy = accuracy_score(labels_te, pred)
      print(f"This is the subset of {value}0% Testing Set")
      print(f"The Accuracy of\t`{iteration}`\tN-Neighbor Value is {pred_accuracy:.2f}")
      confusion = confusion_matrix(labels_te, pred)
      plt.figure(figsize=(6, 4))
      sns.heatmap(confusion, annot=True, cmap='Blues',
                  xticklabels=["No Diabetes, Type 1 Diabetic, Type 2 Diabetic"],
                  yticklabels=["No Diabetes, Type 1 Diabetic, Type 2 Diabetic"])
      plt.title("Confusion Matrix For KNN")
      plt.xlabel("Predicted Label")
      plt.ylabel("True Label")
      plt.show()
      print("\n")
  
  
  # Optimal No. of Neighbors
  features_tr, features_te, labels_tr, labels_te = train_test_split(scaled_features, label, test_size=0.2, random_state=42)
  optimal_k = KNeighborsClassifier(n_neighbors=7)
  optimal_k.fit(features_tr, labels_tr)
  
  optimal_pred = optimal_k.predict(features_te)
  optimal_accuracy = accuracy_score(labels_te, optimal_pred)
  
  print(f"This is the subset of 0.20% Testing Set")
  print(f"The Accuracy of 7 N-Neighbor Value is {optimal_accuracy:.2f}")
  
  confusion = confusion_matrix(labels_te, optimal_pred)
  plt.figure(figsize=(6, 4))
  sns.heatmap(confusion, annot=True, cmap='Blues',
              xticklabels=["No Diabetes, Type 1 Diabetic, Type 2 Diabetic"],
              yticklabels=["No Diabetes, Type 1 Diabetic, Type 2 Diabetic"])
  plt.title("Confusion Matrix For KNN")
  plt.xlabel("Predicted Label")
  plt.ylabel("True Label")
  plt.show()
  print("\n")
  
  
  # Weighted K, uniform and distance weights were assigned.
  features_tr, features_te, labels_tr, labels_te = train_test_split(scaled_features, label, test_size=0.2, random_state=42)
  weights_list = ['uniform', 'distance']
  for weight in weights_list:
    weighted_knn = KNeighborsClassifier(n_neighbors=7, weights=weight)
    weighted_knn.fit(features_tr, labels_tr)
  
    weighted_pred = weighted_knn.predict(features_te)
    weighted_pred_accuracy = accuracy_score(labels_te, weighted_pred)
  
    print(f"This is the subset of 0.20% {weight} method Testing Set")
    print(f"The Accuracy of 7 N-Neighbor value with {weight} method:  is {weighted_pred_accuracy:.2f}")
  
    confusion = confusion_matrix(labels_te, weighted_pred)
    plt.figure(figsize=(6, 4))
    sns.heatmap(confusion, annot=True, cmap='Blues',
                xticklabels=["No Diabetes, Type 1 Diabetic, Type 2 Diabetic"],
                yticklabels=["No Diabetes, Type 1 Diabetic, Type 2 Diabetic"])
    plt.title("Confusion Matrix For KNN")
    plt.xlabel("Predicted Label")
    plt.ylabel("True Label")
    plt.show()
    print("\n")

</details>```