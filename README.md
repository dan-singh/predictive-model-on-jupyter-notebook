# Predict Voice Disorders and Build Bayes Network Model using Jupyter Notebook

## Learning objectives
The goal of this tutorial is to learn how to build a machine learning model in Watson Studio™ using Jupyter notebook.
## Introductin
Disorder attacks the vocal cords hence the voice quality changes; these alterations are the symptoms of voice disorder. Therefore, there has been an incrreasing interest in the objective analysis of the voice to detect disorder. Many applications today rely on machine learning to predict the disorder existance and it's classification. But this tutorial will fixate only in predicting if a disorder exists in the voice. The dataset is obtained from _MEEI_ and processed through the voice box making a unified setting of the recordings to help in the prediction. To extract similar datasets please check the refrences below.

## Prerequisite:
1. Create an IBM Cloud account.
2. Create an instance of Watson Studio from the catalog.

## Estimated time
Walking through this tutorial should take about 10 minutes.

## Flow
<p align="center"><img width="453" alt="flow" src="https://user-images.githubusercontent.com/20974667/46143420-922ff480-c262-11e8-8504-ba727356f24f.PNG">

1. Create an IBM Watson Studio Workspace.
2. Create a Jupyter notebook workplace from the Watson Studio asset.
3. Create a Cloud Object storage to store the data.
4. Jupyter notebook depends on an Apache Spark service.
5. Import data to start building the model


## Steps:
**1- Login to IBM Cloud and Create Watson Studio Service**
1. Register in [IBM Cloud](https://ibm.biz/BdYmuL).
2. Go to **Catalog**.
3. Search for `watson studio`.
4. Click on the service and then **Create**.
5. On the service page, click on **Get Started**.

**2- Create a project in IBM Watson platform.**
1. Scrol down the page and click on **(+) New project icon**.
2. Name your project 'Predict loan eligibility'.
3. Click **Create**.
4. In your project page, nagivate to the Assests tab, drag the [samples dataset](https://github.com/Meaad96s/predictive-model-on-jupyter-notebook/blob/master/n_samples.csv) and [targets dataset](https://github.com/Meaad96s/predictive-model-on-jupyter-notebook/blob/master/n_features.csv) files and drop it in the Load sidebar.


<p align="center"><img  src="https://user-images.githubusercontent.com/20974667/45819331-b9c80f80-bcec-11e8-8c9b-81389c55cc4c.png">
  

**3- Create a Notebook Jupyter from the assets tab.**

Language: Python 3.5 with spark
Spark version: Spark 2.3

<p align="center"><img  src="https://user-images.githubusercontent.com/20974667/45819333-b9c80f80-bcec-11e8-9ac5-1f961abde16d.png">

**40 Press the pen icon to edit the notebook**

<p align="center"><img  src="https://user-images.githubusercontent.com/20974667/45819335-b9c80f80-bcec-11e8-9690-2cc059dc699f.png">

###

**5- From the left bar, insert the code to import the samples data from data asset**
<p align="center"><img  src="https://user-images.githubusercontent.com/20974667/45819336-b9c80f80-bcec-11e8-9562-a12240dbe17a.png">
  
and change the shape of the dataframe to 
`X=np.reshape(df_data, (226, 12))` 

Then do it again in another Cell to inser the code of importing the targets dataset.
The matrix of the targets dataset is 1D so it must be changed to
`y=np.ravel(df_target)`

**6- Cross Validation**
Import train and test split from Sklearn for cross validation
The folds of cross validation for this lab is 10.

> you can take the snippet below
```

from sklearn.cross_validation import train_test_split
X_train, X_test, y_train, y_test = train_test_split(df_data, df_target, test_size=0.33, random_state=42)
y_train=np.ravel(y_train)
from sklearn.model_selection import KFold
kf = KFold(n_splits=10) # Define the split - into 2 folds 
kf.get_n_splits(X) # returns the number of splitting iterations in the cross-validator
```

#### So,each dataset is split to train and test groups.

**7- Build the Model**
The machine learning model is Support Vector Machine SVM.
> The snippet below is how to build a model giving training dataset of samples and tartets as parameters.
```
from sklearn import svm
clf = svm.SVC()
clf.fit(X_train,y_train )
y_pred = clf.fit(X_train, y_train).predict(X_test)
```
**8- Model Score**
View the Accuracy of the model in the course of 10 times of runs using the snippet below.

<p align="center"><img width="368" alt="scores" src="https://user-images.githubusercontent.com/20974667/46256053-f1357980-c4ad-11e8-89f4-faee77d0992d.PNG">
 
```
from sklearn.cross_validation import cross_val_score, cross_val_predict
scores = cross_val_score(clf, X, y, cv=10)
print (scores)
```
These scores can be multipled by 100% to show the percentage of well predicted recordings. The more it is close to 100% the more accuracte the model is.

## Summary
This tutorial explains how an _automatic speech recognition_ is done and using machine learning techniques.The model accuracy shows a high accuracy which result in a reliable predictive model. Picture below evaluate the model score of both training and test recording in accordance to the gamma value of the model. The x-axis which represents accuracy score has values from 20% to 100%.

<p align="center"><img width="241" alt="eva" src="https://user-images.githubusercontent.com/20974667/46256046-e11d9a00-c4ad-11e8-8b5b-9b920e6b4d05.PNG">



## References
1. Massachusetts Eye and Ear Infirmary. (1994). Voice Disorders Database. Lincoln Park, NJ: Kay Elemetrics Corp.
2. http://www.stimmdatenbank.coli.uni-saarland.de/index.php4#target
3. Watson Studio: Master the art of data science with IBM’s [Watson Studio](https://eu-gb.dataplatform.ibm.com/home?context=analytics).


## License
GNU General Public License v3.0
