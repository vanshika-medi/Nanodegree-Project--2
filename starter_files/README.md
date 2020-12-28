

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

![Registered Dataset](https://user-images.githubusercontent.com/68374253/103230729-2adede80-495c-11eb-964a-a983d5d0726b.png)


# AutoML Run

Create AutoML run by creating a compute cluster after specifying minimum and maximum nodes. This takes about 30 mins to produce models. In this case the best model was VotingEnsemble.

* Completed run:

![Completed run](https://user-images.githubusercontent.com/68374253/103230779-4b0e9d80-495c-11eb-9b8a-4afd367c7783.png)

* Completed run status:

![Completed automl run](https://user-images.githubusercontent.com/68374253/103230828-64afe500-495c-11eb-9f4c-c79b143bb6c3.png)

* Top models:

![Top best models](https://user-images.githubusercontent.com/68374253/103230860-785b4b80-495c-11eb-81db-5c3a478d3b83.png)

* Best Model *VotingEnsemble* :

![Best model](https://user-images.githubusercontent.com/68374253/103230892-85783a80-495c-11eb-947b-621f20d13f7b.png)

# Deploy the best model

The best model is *VotingEnsemble*. To deploy this, we add a deploy name, description, compute type which in this case is *Azure Container Instance* and enable authentication.
*Azure Container Instance* uses container technology to quickly deploy compute instances. It is simpler to use and flexibility is reduced as compared to *Azure Kubernetes Services*.
* Deploying details:

![Deploying](https://user-images.githubusercontent.com/68374253/103230999-c40df500-495c-11eb-8d29-ec8984a7cb66.png)

* Deployed model:

![Deploy_details](https://user-images.githubusercontent.com/68374253/103231031-d7b95b80-495c-11eb-9b52-8504aae99d35.png)

![Deploy_details_1](https://user-images.githubusercontent.com/68374253/103231099-02a3af80-495d-11eb-8413-3567ff05ab90.png)

* Deploy model endpoint:

![Deployed model endpoint](https://user-images.githubusercontent.com/68374253/103231126-13542580-495d-11eb-94b9-3a990048a18c.png)

# Logging

Application insights is a useful tool to detect anomalies and visualize performance. Running the script logs.py provides informational output produced by the software, i.e. logs.

* Logs:

![logs](https://user-images.githubusercontent.com/68374253/103231150-236c0500-495d-11eb-8318-0668bd5ee9b6.png)

* Application Insights:

![Application insights](https://user-images.githubusercontent.com/68374253/103231190-3da5e300-495d-11eb-8c9c-f0ef81c6f97e.png)

* Enabled Insights:

![Application insights enabled](https://user-images.githubusercontent.com/68374253/103231173-3088f400-495d-11eb-9faa-5cf091c45e7f.png)

# Consume Endpoints

Swagger helps build, document, and consume web services. Here we run *swagger.sh* file and *serve.py* with the port address as 9001. It gives the following API on the address http://localhost:9001/:

* Downloading swagger.json

![Downloading swagger](https://user-images.githubusercontent.com/68374253/103231449-cd4b9180-495d-11eb-936d-08a4b84e8988.png)

* Docker Running:

![Docker running](https://user-images.githubusercontent.com/68374253/103231265-6928cd80-495d-11eb-82fa-3106ed8f700b.png)

* Swagger API:

![Swagger api](https://user-images.githubusercontent.com/68374253/103231330-88275f80-495d-11eb-88a2-a35c7d74723a.png)

![Swagger_api_1](https://user-images.githubusercontent.com/68374253/103231335-89f12300-495d-11eb-8be7-1843a5bc63ec.png)

![Swagger_api_2](https://user-images.githubusercontent.com/68374253/103231341-8bbae680-495d-11eb-85ab-33fa2c91fbbd.png)

![Swagger_api_3](https://user-images.githubusercontent.com/68374253/103231343-8c537d00-495d-11eb-82b8-2b6be2b44fcf.png)

* Python Endpoint for Run

![python endpoint (2)](https://user-images.githubusercontent.com/68374253/103231746-9de95480-495e-11eb-82ee-d80c61328409.png)

# Publish Pipeline:

The steps to publishing pipeline is given in the .ipynb file.

* Pipeline run overview:

![Pipeline run overview](https://user-images.githubusercontent.com/68374253/103231451-cf155500-495d-11eb-9f66-dd54fbbfef82.png)

* Pipeline Published Overview:

![Published pipeline overview](https://user-images.githubusercontent.com/68374253/103231455-d0468200-495d-11eb-9dcb-893771edf345.png)

![Published pipeline overview_2](https://user-images.githubusercontent.com/68374253/103231456-d0df1880-495d-11eb-9602-424901cb506e.png)

* Completed Pipelines:

![Pipelines](https://user-images.githubusercontent.com/68374253/103231454-cfadeb80-495d-11eb-8613-a12eb049320f.png)

* Status as "Active":

![Status Active](https://user-images.githubusercontent.com/68374253/103231460-d2104580-495d-11eb-8d0b-19069efde548.png)

![Active status in notebook](https://user-images.githubusercontent.com/68374253/103231905-03d5dc00-495f-11eb-8250-bdb598913e15.png)

# Documentation: Screen Recording

The recording of the documentation is here: [Screencast](https://youtu.be/RmOAkKa0MEE)

# Standount Suggestions

AutoML has all parameters needed for a good model deployment and training. However in the AutoML config class while publishing the pipeline, we can give featurization parameters instead of setting it to "auto".
