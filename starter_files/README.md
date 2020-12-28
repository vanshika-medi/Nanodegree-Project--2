

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


# AutoML Run

Create AutoML run by creating a compute cluster after specifying minimum and maximum nodes. This takes about 30 mins to produce models. In this case the best model was VotingEnsemble.



These are the top models.

# Deploy the best model

The best model is *VotingEnsemble*. To deploy this, we add a deploy name, description, compute type which in this case is *Azure Container Instance* and enable authentication.
*Azure Container Instance* uses container technology to quickly deploy compute instances. Simpler to use and flexibility is reduced as compared to AKS.
* Deploying the model:


* Deployed model:



# Logging

Application insights is a useful tool to detect anomalies and visualize performance. Running the script logs.py provides informational output produced by the software, i.e. logs.

* Logs:


* Application Insights:


* Enabled Insights:


# Consume Endpoints

* Swagger helps build, document, and consume web services. Here we run *swagger.sh* file and *serve.py* with the port address as 9001. It gives the following API on the address http://localhost:9001/:



# Publish Pipeline:

The steps to publishing pipeline is given in the .ipynb file.

* Pipeline graph:



* Completed Pipelines:



* Status as "Active":



* Published Pipeline Overview






# Documentation: Screen Recording

The recording of the documentation is here: [Screencast](https://youtu.be/v4pCaA3LZIw)

# Standount Suggestions

AutoML has all parameters needed for a good model deployment and training. However in the AutoML config class while publishing the pipeline, we can give featurization parameters instead of setting it to "auto".
