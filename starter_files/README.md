*NOTE:* This file is a template that you can use to create the README for your project. The *TODO* comments below will highlight the information you should be sure to include.


# Operationalizing Machine Learning

The objective of this project is to train, deploy and work with Machine Learning through Microsoft Azure.

## Dataset

The dataset we are provided with is the Bank Marketing Dataset. The aim is to predict "y" which is whether a person would subscribe to a deposit or not based on the client information like age, marital status, job, education etc. This makes it a classification problem.

## Architectural Diagram

![Architecture](https://user-images.githubusercontent.com/68374253/103178599-3245af80-48aa-11eb-8b65-c671dde28497.png)

According to the flowchart, we see there are 7 steps each of which are descibed in the next section.


## Key Steps

# Authentication

The first step is authentication however since the Udacity lab was being used, I did not follow that step.

# Registering Dataset

The dataset to be registered is bank-marketing. Attached below is the screenshot for it. This is a vital step as all the other steps follow through after this.

![Registered Dataset](https://user-images.githubusercontent.com/68374253/103178669-d3cd0100-48aa-11eb-9bac-9c2988c07577.png)

# AutoML Run

Create AutoML run by creating a compute cluster after specifying minimum and maximum nodes. This takes about 30 mins to produce models. In this case the best model was VotingEnsemble.


![Models](https://user-images.githubusercontent.com/68374253/103178780-fe6b8980-48ab-11eb-905b-8bdf7072e9ee.png)

These are the top models.

# Deploy the best model

The best model is *VotingEnsemble*. To deploy this, we add a deploy name, description, compute type which in this case is *Azure Container Instance* and enable authentication.
*Azure Container Instance* uses container technology to quickly deploy compute instances. Simpler to use and flexibility is reduced as compared to AKS.
* Deploying the model:

![Deploying the model](https://user-images.githubusercontent.com/68374253/103178831-910c2880-48ac-11eb-8511-902863c644c3.png)

* Deployed model:

![Deployed model](https://user-images.githubusercontent.com/68374253/103178867-cfa1e300-48ac-11eb-876f-88aa5f3b6451.png)

# Logging

Application insights is a useful tool to detect anomalies and visualize performance. Running the script logs.py provides informational output produced by the software, i.e. logs.

* Logs:

![Logs](https://user-images.githubusercontent.com/68374253/103178906-1394e800-48ad-11eb-9444-187b31812013.png)

* Application Insights:

![Application insights enabled](https://user-images.githubusercontent.com/68374253/103178913-332c1080-48ad-11eb-8914-3556703a6c6f.png)

* Enabled Insights:

![Enabled insights](https://user-images.githubusercontent.com/68374253/103178933-5060df00-48ad-11eb-97cd-a43206c0e44d.png)

# Consume Endpoints

* Swagger helps build, document, and consume web services. Here we run *swagger.sh* file and *serve.py* with the port address as 9001. It gives the following API on the address http://localhost:9001/:

![Swagger page](https://user-images.githubusercontent.com/68374253/103179030-09271e00-48ae-11eb-8f88-5e3127a4c1f8.png)

# Publish Pipeline:

The steps to publishing pipeline is given in the .ipynb file.

* Pipeline graph:

![pipeline graph](https://user-images.githubusercontent.com/68374253/103179072-602cf300-48ae-11eb-9141-77b4b9892501.png)

* Completed Pipelines:

![Completed pipelines](https://user-images.githubusercontent.com/68374253/103179088-8357a280-48ae-11eb-8bab-f78294a9792d.png)

* RunDetails:

![Run Details](https://user-images.githubusercontent.com/68374253/103179109-a1250780-48ae-11eb-8d5a-582b50df1aec.png)

![Pipeline endpoint](https://user-images.githubusercontent.com/68374253/103179142-e3e6df80-48ae-11eb-9f84-d22d64d0505c.png)

![REST Endpoint](https://user-images.githubusercontent.com/68374253/103179123-c0239980-48ae-11eb-9193-6decea478830.png)

![python endpoint](https://user-images.githubusercontent.com/68374253/103179128-c9ad0180-48ae-11eb-8fa4-b3aaa2459c00.png)




# Documentation: Screen Recording

The recording of the documentation is here: [Screencast](https://youtu.be/v4pCaA3LZIw)

