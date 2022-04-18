# Data Science<br>Exercise 5 - Comparative Experimentation

<br/>Student: se21m024, Thomas Stummer
<br/><br/>The source code can be found in the document <b><i>se21m024_Stummer_ex5_comp_exp.ipynb</i></b>.
<br/><br/>
Small data set: Heart Failure Prediction<br>
The data set was provided by Davide Chicco, Giuseppe Jurman: Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone. BMC Medical Informatics and Decision Making 20, 16 (2020) (https://bmcmedinformdecismak.biomedcentral.com/articles/10.1186/s12911-020-1023-5) and downloaded from https://www.kaggle.com/datasets/andrewmvd/heart-failure-clinical-data.
<br/><br/>
Big data set: Covertype<br>
The data set was provided by Jock A. Blackard and Colorado State University and downloaded from https://archive.ics.uci.edu/ml/datasets/Covertype.
<br/><br/>

<div style="page-break-after: always"></div>

# Small data set: Heart Failure Prediction

Results table for heart failure prediction (training and testing time in seconds)

| Algorithm with parameters          | Accuracy | Precision | Training time | Testing time |
| ---------------------------------- | -------- | --------- | ------------- | ------------ |
| k-NN (5-NN)                        | 0.616    | 0.616     | 0.001632      | 0.007975     |
| k-NN (10-NN)                       | 0.677    | 0.677     | 0.001979      | 0.004032     |
| k-NN (15-NN)                       | 0.687    | 0.687     | 0.001962      | 0.004039     |
| Perceptron (alpha: 0.0001)         | 0.687    | 0.687     | 0.004009      | 0.001991     |
| Perceptron (alpha: 0.001)          | 0.687    | 0.687     | 0.001948      | 0.001013     |
| Perceptron (alpha: 0.01)           | 0.687    | 0.687     | 0.002556      | 0.001        |
| Decision tree (max features: None) | 0.697    | 0.697     | 0.002458      | 0.00192      |
| Decision tree (max features: auto) | 0.626    | 0.626     | 0.00152       | 0.002036     |
| Decision tree (max features: sqrt) | 0.626    | 0.626     | 0.002008      | 0.001011     |
| Decision tree (max features: log2) | 0.626    | 0.626     | 0.001973      | 0.001999     |

# Big data set: Covertype

Results table for covertype prediction (training and testing time in seconds)

| Algorithm with parameters          | Accuracy | Precision | Training time | Testing time |
| ---------------------------------- | -------- | --------- | ------------- | ------------ |
| k-NN (5-NN)                        | 0.965    | 0.965     | 11.612576     | 17.819602    |
| k-NN (10-NN)                       | 0.955    | 0.955     | 11.56541      | 24.748777    |
| k-NN (15-NN)                       | 0.946    | 0.946     | 11.596502     | 30.529842    |
| Perceptron (alpha: 0.0001)         | 0.584    | 0.584     | 9.940245      | 0.086659     |
| Perceptron (alpha: 0.001)          | 0.584    | 0.584     | 9.795955      | 0.043014     |
| Perceptron (alpha: 0.01)           | 0.584    | 0.584     | 9.463287      | 0.046001     |
| Decision tree (max features: None) | 0.933    | 0.933     | 5.5636        | 0.079001     |
| Decision tree (max features: auto) | 0.877    | 0.877     | 1.156122      | 0.084002     |
| Decision tree (max features: sqrt) | 0.877    | 0.877     | 1.158357      | 0.082988     |
| Decision tree (max features: log2) | 0.87     | 0.87      | 0.94755       | 0.085998     |
