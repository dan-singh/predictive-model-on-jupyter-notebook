# Predict Voice Disorders and Build Bayes Network Model using Jupyter Notebook

Flow


1. Create an IBM Watson Studio Workspace.
2. Create a Jupyter notebook workplace from the Watson Studio asset.
3. Create a Cloud Object storage to store the data.
4. Jupyter notebook depends on an Apache Spark service.
5. Import data to start building the model


## Prerequisite:
1. Create an IBM Cloud account.
2. Create an instance of Watson Studio from the catalog.

# Steps:
**Login to IBM Cloud and Create Watson Studio Service**
1. Register in [IBM Cloud](https://ibm.biz/BdYmuL).
2. Go to **Catalog**.
3. Search for `watson studio`.
4. Click on the service and then **Create**.
5. On the service page, click on **Get Started**.

**Create a project in IBM Watson platform.**
1. Scrol down the page and click on **(+) New project icon**.
2. Name your project 'Predict loan eligibility'.
3. Click **Create**.
4. In your project page, nagivate to the Assests tab, drag the [data set samples](https://github.com/Meaad96s/predictive-model-on-jupyter-notebook/blob/master/n_samples.csv) and [data set targets](https://github.com/Meaad96s/predictive-model-on-jupyter-notebook/blob/master/n_features.csv) files and drop it in the Load sidebar

**Create a Notebook Jupyter from the assets tab.**

Run the notebook in IBM Data Science Experience
Deploy the saved predictive model as a scoring service

## References
Watson Studio: Master the art of data science with IBM’s Watson Studio.

## License
GNU General Public License v3.0
