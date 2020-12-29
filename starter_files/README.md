

# Operationalizing Machine Learning

# Overview

The objective of this project is to train, deploy and work with Machine Learning through Microsoft Azure. We learn to deploy, authenticate, create and check logs, and use the deployed model as the REST API.
We will deploy a model in an ACI (Azure Container Instance). ACIs in Azure Machine Learning are meant to be used for development and testing purposes, as they only support low-scale workloads on CPUs. Yet, they can make use of up to 16GB of RAM and 4 CPUs. After deploying a model the web service will appear in the Azure Machine Learning portal, under the Endpoints section. There, we can obtain its REST endpoint’s URI which we use to interact with the model.
We deploy a model in two different ways. First we use Automated ML in the Azure ML platform and than we use the Python SDK to create a pipeline with AutoML steps.

## Dataset

The dataset we are provided with is the Bank Marketing Dataset. The aim is to predict "y" which is whether a person would subscribe to a deposit or not based on the client information like age, marital status, job, education etc. This makes it a classification problem since the output would be either "yes" or "no".

## Architectural Diagram

![Architecture](https://user-images.githubusercontent.com/68374253/103178599-3245af80-48aa-11eb-8b65-c671dde28497.png)

According to the flowchart, we see there are 7 steps each of which are descibed in the next section.


## Key Steps

# Authentication

The first step is authentication however since the Udacity lab was being used, I did not follow that step.

# Registering Dataset

The dataset to be registered is bank-marketing. Attached below is the screenshot for it. This is a vital step as all the other steps follow through after this.

![Registered Dataset](https://user-images.githubusercontent.com/68374253/103301816-2ed83280-4a28-11eb-809d-f98ea87d669f.png)


# AutoML Run

Create AutoML run by creating a compute cluster after specifying minimum and maximum nodes. This takes about 30 mins to produce models. In this case the best model was VotingEnsemble.

* Completed run:

![AutoML Run Complete](https://user-images.githubusercontent.com/68374253/103301877-562eff80-4a28-11eb-8d12-9c032a02339f.png)

* Completed run status:

![AutoML Run Complete_1](https://user-images.githubusercontent.com/68374253/103301882-58915980-4a28-11eb-857a-ca44871f0828.png)

* Top models:

![Top Models](https://user-images.githubusercontent.com/68374253/103301889-5af3b380-4a28-11eb-88e2-f9429ee36ba9.png)

* Best Model *VotingEnsemble* :

![Best Model](https://user-images.githubusercontent.com/68374253/103301883-59c28680-4a28-11eb-8fa7-9c82758ceca5.png)

# Deploy the best model

The best model is *VotingEnsemble*. To deploy this, we add a deploy name, description, compute type which in this case is *Azure Container Instance* and enable authentication.
*Azure Container Instance* uses container technology to quickly deploy compute instances. It is simpler to use and flexibility is reduced as compared to *Azure Kubernetes Services*.

* Deploying details:

![rds](https://user-images.githubusercontent.com/68374253/103302072-c50c5880-4a28-11eb-9cf3-04b74c4b506d.png)

* Deployed model:

![Deployed model_1](https://user-images.githubusercontent.com/68374253/103302034-b02fc500-4a28-11eb-9f0e-6ae906b5fe7b.png)

![Deployed model_2](https://user-images.githubusercontent.com/68374253/103302035-b0c85b80-4a28-11eb-8850-328f3c00bc0a.png)

* Deploy model endpoint:

![Deployed model](https://user-images.githubusercontent.com/68374253/103302032-ae660180-4a28-11eb-956a-d1ab7d69642d.png)

* Consume Details:

![Consume Details](https://user-images.githubusercontent.com/68374253/103302030-ad34d480-4a28-11eb-80ce-d7bab249b67b.png)

# Logging

Application insights is a useful tool to detect anomalies and visualize performance. Running the script logs.py provides informational output produced by the software, i.e. logs.

* Logs:

![Logs running](https://user-images.githubusercontent.com/68374253/103302193-10bf0200-4a29-11eb-9dc4-f3775628dc40.png)

* Application Insights:

![Application Insights](https://user-images.githubusercontent.com/68374253/103302190-0f8dd500-4a29-11eb-8cb7-601cb0ea4234.png)


# Consume Endpoints

Swagger helps build, document, and consume web services. Here we run *swagger.sh* file and *serve.py* with the port address as 9001. It gives the following API on the address http://localhost:9001/:

* Downloading swagger.json

![Downloading Swagger](https://user-images.githubusercontent.com/68374253/103302340-6c898b00-4a29-11eb-98b4-9d8daf44a7e6.png)

* Docker Running:

![Docker running](https://user-images.githubusercontent.com/68374253/103302435-ac507280-4a29-11eb-8aa8-07f5f40b8b54.png)

* Swagger API:

![Swagger_api](https://user-images.githubusercontent.com/68374253/103302350-727f6c00-4a29-11eb-8376-8ffb54b16bfc.png)

![Swagger_api_1](https://user-images.githubusercontent.com/68374253/103302354-757a5c80-4a29-11eb-84a2-73a3fc83f499.png)

![Swagger_api_2](https://user-images.githubusercontent.com/68374253/103302357-77dcb680-4a29-11eb-9508-5eb26c2c1eaf.png)

![Swagger_api_3](https://user-images.githubusercontent.com/68374253/103302362-790de380-4a29-11eb-9191-77ca98c04eea.png)

* Editing endpoint.py with REST Endpoint and key

![edited endpoint file](https://user-images.githubusercontent.com/68374253/103302344-6f847b80-4a29-11eb-8947-52d89c0c6325.png)

* Python Endpoint for Run

![Running endpoint](https://user-images.githubusercontent.com/68374253/103302348-714e3f00-4a29-11eb-8b41-55f29b8b3b47.png)


# Publish Pipeline:

The steps to publishing pipeline is given in the .ipynb file.

* Pipeline run overview:

![Pipeline Run Overview](https://user-images.githubusercontent.com/68374253/103302546-f2a5d180-4a29-11eb-8bf0-809f1099ea2f.png)

* Pipeline Published Overview:

![Published Pipeline Overview](https://user-images.githubusercontent.com/68374253/103302553-f5a0c200-4a29-11eb-8d10-0a02b91e5b5a.png)

* Completed Pipelines:

![Pipelines run](https://user-images.githubusercontent.com/68374253/103302549-f3d6fe80-4a29-11eb-9879-2ab40a830a77.png)

* Status as "Active":

![Status Active](https://user-images.githubusercontent.com/68374253/103302561-f8031c00-4a29-11eb-9f76-385969934409.png)

* RunWidgets:

![RunWidgets](https://user-images.githubusercontent.com/68374253/103302559-f6d1ef00-4a29-11eb-9ef3-f136d4bb2f8b.png)

![Rest Endpoint Active](https://user-images.githubusercontent.com/68374253/103302557-f6395880-4a29-11eb-9c6f-351946f2b9ba.png)

# Documentation: Screen Recording

The recording of the documentation is here: [Screencast](https://youtu.be/cGkNaw-5gCg)

# Standount Suggestions

* AutoML has all parameters needed for a good model deployment and training. However in the AutoML config class while publishing the pipeline, we can give featurization parameters instead of setting it to "auto".
* We can also manage imbalanced data and prevent overfitting with AutoML by better regularization of hyperparameters and try to identify overfitting.
