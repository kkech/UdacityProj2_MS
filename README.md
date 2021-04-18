
# Udacity Nanodegree Project 2

## Table of Contents
* ### Overview
* ### Architectural Diagram
* ### Key Steps
     * Automated ML Experiment 
     * Deploy the best model
     * Enable App Insights & Logging
     * Swagger Documentation
     * Consume model endpoints
     * Create and publish a pipeline
* Screen Recording
* Standout Suggestions
* References

## Overview
This projects aims to create a cloud-based machine learning model for the Bank Marketing Dataset, which contains data about marketing campaigns for a bank. We will utilize AutoML for this classification problem. This will let us predict whether a bank product would be subscribed by the client or not.  
The project involves:
* Automated ML Experiment
* Deploy the best model
* Enable logging
* Swagger Documentation
* Consume model endpoints
* Create and publish a pipeline

## Architectural Diagram
The diagram below illustrates the keys steps of our operation:
![Architecture](https://github.com/kkech/UdacityProj2_MS/blob/master/architectureDiagram.png) 

* We will use Bank Marketing Dataset to create an AutoML. The AutoML will help up find the best model and the best parameters to fit our data. 
* We use the model obtained by the AutoML to train an ML pipeline.
* We publish the model and the pipeline in order to be ready for consumption. 

## Key Steps

### Step 1: Automated ML Experiment
We first upload our dataset using the dataset's URI:
![Dataset](https://github.com/kkech/UdacityProj2_MS/blob/master/RegisteredDataset.png)  

After the run is complete, we're able to determine the best model which is the **Voting Ensemble** with accuracy of **0.91988**:
![Best Model](https://github.com/kkech/UdacityProj2_MS/blob/master/AutoMlModelsAcc.png)  

### Step 2: Deploy the best model
We deploy the Voting Ensemble model, which is the best model, using Azure Container Instacne (ACI) while making sure that the Authentication option enabled.
![Deployment](https://github.com/kkech/UdacityProj2_MS/blob/master/deployedModel.png)  


### Step 3: Enable App Insights & Logging
In order to enable Application Insights programmatically, we edited the logs.py script to match the deployed model ID and change App Inights to TRUE. Then, we run the python script.
![App Insights](https://github.com/kkech/UdacityProj2_MS/blob/master/appInsEnabled.png)  

Screenshots of Logs:
![Logs](https://github.com/kkech/UdacityProj2_MS/blob/master/appInsLog.png) 

### Step 4: Swagger Documentation
In this step, we setup Swagger to be able to deploy and consume model.
We downloaded swagger.json file from deployed model on Azure. Then we ran swagger.sh and serve.py script on Powershell command window.
![Swagger](https://github.com/kkech/UdacityProj2_MS/blob/master/swaggerModel.png) 


### Step 5: Consume model endpoints  
Then we used endpoint.py script to consume the model endpoints. We first edited the *scoring_uri* and the *key* in the script to match the URI and the key of our service. Then, we executed endpoint.py script.
![Endpoint](https://github.com/kkech/UdacityProj2_MS/blob/master/endpointCall.png) 

Also, we benchmark the endpoint using Apache bench.
![Benchmark](https://github.com/kkech/UdacityProj2_MS/blob/master/ab1.png)
![Benchmark](https://github.com/kkech/UdacityProj2_MS/blob/master/ab2.png) 

### Step 6: Create and publish a pipeline
In this step, we first updated our jupyter notebook variables to match our azure enviroment variables. 
Then, we deployed our training pipeline and published it. 

Pipeline Endpoint:
![Pipeline](https://github.com/kkech/UdacityProj2_MS/blob/master/pipelineEndpoint.png) 

Bankingmarketing dataset with AutoML module:
![Pipeline](https://github.com/kkech/UdacityProj2_MS/blob/master/bankMarketDataset__AND__PublishedPipeline.png) 

Published Pipeline Overview:
![Pipeline](https://github.com/kkech/UdacityProj2_MS/blob/master/bankMarketDataset__AND__PublishedPipeline.png) 

Run Details Widget:
![Pipeline](https://github.com/kkech/UdacityProj2_MS/blob/master/scheduledRun.png)

Scheduled Run:
![Pipeline](https://github.com/kkech/UdacityProj2_MS/blob/master/scheduledRun.png)


## Screen Recording
[Screencast](https://youtu.be/qmUmhM-7Qk0)

My screen is in full screen mode at 1080p and 16:9 aspect ratio. I used OBS for the recording.

## Future Improvements
* We can increase the Exit Criterion time from 1 hour to the default value of 3 hours to be able to find models of higher accuracy.
* We can enable deep learning in AutoML
* We can  enable Data drift tracking to ensure accuracy of the model.
