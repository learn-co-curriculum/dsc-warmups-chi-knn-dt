```python
#run this cell as-is
import pandas as pd
import numpy as np
from sklearn.datasets import make_classification
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import f1_score

import matplotlib.pyplot as plt
%matplotlib inline

#used for tests
from test_scripts.test_class import Test
test = Test()

data = test.load_ind('data')

X = data.drop('target', axis=1, inplace=False)
y = data['target']
```

### Complete the following code which:

- Performs a train-test split
  - test data is 20% of total data, `random_state` of 34

- creates StandardScaler and KnnClassifier objects

- scales the train and test data (correctly!)

- Sets up a loop which
  - sets the `n_neighbors` attribute in the knn object to the current iteration of the loop
     - (Why do we only include odd k values?  Why do we start with 3?)
  - fits the knn object on the training data
  - makes predictions on the test data
  - finds the f1_score of the test data
  - appends that score to `knn_scores`, a hither-to empty list
  
The code following the loop graphs the f1_score by k value, no need to alter anything in there

Graph should look like this:

![](test_obj/viz.png)


```python
#complete the following code

X_train, X_test, y_train, y_test = ########

scaler = ########
knn = ########

X_train_scl = ########

X_test_scl = ########

knn_scores = []

for k in (3,20,2):

    knn = knn.set_params(n_neighbors=######)
    
    knn.fit(########)
    knn_preds = ########
    
    knn_score = f1_score(########)
    
    knn_scores.append(##########)
    
fig, ax = plt.subplots()
ax.plot([x for x in range(3,20,2)], knn_scores)
ax.set_xticks([x for x in range(3,20, 2)])
ax.set_xlabel('k')
ax.set_ylabel('test f1 score')
ax.set_title('test f1 score for each odd value of k')
plt.plot();
```

### Which value of k should we choose as our model?


```python
'''
Your answer here
'''
```
