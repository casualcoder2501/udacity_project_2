# Udacity Project 2: Pipelines and Deployment

## Overview

This objective of this project was to learn how to use Azure ML Studio to deploy and consume both autoML pipelines and stand-alone models. Swagger and Apache Benchmark were other technologies that were utilized for this project to both aid in documentation of the endpoint and testing the endpoint's capabilities in responding to user requests respectively. The dataset used was marketing information for a bank that contained customer demographics and contact times. The AutoML model and Pipeline attempted to predict the 'y' column which represented if the customer subscribed to a term deposit or not. Using a classification model we acheived 91.7% accuracy in predicting outcomes. The model was then deployed to an Azure Container Instance and consumed using a brief python script or Jupyter Notebook for testing. This same experiment was used to build a pipeline which we then deployed and tested. The purpose of the final pipeline was to demostrate the power of automating an ML process that could then be kicked off simply by posting to a deployed endpoint.

## Architectural Diagram
![image](https://user-images.githubusercontent.com/28558135/134224041-fe1e07b8-b8d9-4dbd-adcf-f111783bd4e4.png)

## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screenshots required to demonstrate key steps.
### Created a Service Principle and Assigned Admin Role
<img width="725" alt="azure-az-auth" src="https://user-images.githubusercontent.com/28558135/134102097-3caf1210-9a0c-40e6-8ba7-ac52741468f3.png">

Using the az commandline tool I created an SP for Azure ML

<img width="633" alt="azure-ml-workspace-share" src="https://user-images.githubusercontent.com/28558135/134102268-dce6a1c7-79b7-4c95-b42d-8d9f8015c1d5.png">

Using the workspace share command I assigned the previously created SP to the role of admin

### Dataset Registration and AutoML Model Training
<img width="2032" alt="banking_data_registered" src="https://user-images.githubusercontent.com/28558135/134102392-ae86d79b-ea0d-40e2-ac73-423ab567a293.png">

The banking data was registered as a dataset prior to running the AutoML experiment

<img width="2036" alt="banking_experiment_completed" src="https://user-images.githubusercontent.com/28558135/134102883-a4adeb42-c7dd-442c-a951-53a8a10ca43c.png">

The experiment yielded a model with an accuracy of .917 and this is the model that was deployed to the endpoint
<img width="2036" alt="banking_best_model_completed" src="https://user-images.githubusercontent.com/28558135/134103014-ffb455ee-51a5-4777-8815-cdbea471fcc4.png">


### Capturing Logs and Enabling Application Insights
<img width="2007" alt="azure-logs-output" src="https://user-images.githubusercontent.com/28558135/134103168-6193078e-8936-471d-a173-a42cb2740cd2.png">

This was pretty straight forward. I included the code for enabling application insights with the code that gave the log output.

<img width="1845" alt="azure-application-insights" src="https://user-images.githubusercontent.com/28558135/134103253-2b2189d4-1684-41fb-a01b-03a1af2c374c.png">

### Swagger Documentation and Apache Benchmarking

<img width="2024" alt="swagger-local-host" src="https://user-images.githubusercontent.com/28558135/134103316-11c3e7cd-d126-4f84-a52d-21331d61385d.png">

The Swagger.json was downloaded and used to serve the swagger endpoint documentation on the local host. After this the Apache Benchmarking was run to ensure that the endpoint was receiving and outputing the correct json data.

<img width="1963" alt="endpoint-result" src="https://user-images.githubusercontent.com/28558135/134103440-00345ea1-ab62-451f-9a41-0cf32b52e8d9.png">

<img width="1174" alt="apache_benchmark" src="https://user-images.githubusercontent.com/28558135/134103463-8c1c4d54-7bf9-4887-bd0c-337f912ab53a.png">

### Creating, Publishing, and Consuming The Pipeline

<img width="2006" alt="pipeline_created" src="https://user-images.githubusercontent.com/28558135/134103598-43b257e7-ada4-4707-8664-6b4997f468cc.png">

<img width="2018" alt="pipeline_endpoint" src="https://user-images.githubusercontent.com/28558135/134103620-8e2ce7bf-99a2-4f82-a481-901872598936.png">

The pipeline was creating using the previously run AutoML experiment using the banking data and the best run was deployed to an endpoint. 
<img width="2031" alt="banking_data_mlmodule" src="https://user-images.githubusercontent.com/28558135/134103652-c5ee7eee-3eb6-4e14-8ff6-950a741bf506.png">

<img width="2008" alt="pipeline_endpoint_overview" src="https://user-images.githubusercontent.com/28558135/134103701-400e7364-5a80-4cc9-b4a8-bd823894002e.png">

After publishing the pipeline the pipeline endpoint could be viewed from the Pipelines Section of AutoML

<img width="1660" alt="jupyter_rundetails" src="https://user-images.githubusercontent.com/28558135/134103722-90c7fab5-6d74-4629-b8a6-c84d4e3827b3.png">

The RunDetails would not run in the Azure Notebooks environment so I had to open the notebook in the Jupyter Editor to see the output of the rundetails. I did not have this issue with the previous project and further investigation would aid in a future experiment.

<img width="2040" alt="scheduled_run" src="https://user-images.githubusercontent.com/28558135/134103748-ffbcbf61-e5a5-433f-bee0-2bed30905f8e.png">

The pipeline was consumed and kicked off to ensure that the endpoint was functioning properly and compeleted successfully.

## Screen Recording
https://youtu.be/_WSIqnUVAlc

## Standout Suggestions

The Swagger documentation required that I include the swagger folder in the path after localhost:8000. For some reason the server was serving it from 1 level up from the swagger folder even though both the serve.py and swagger.json files were located in the swagger folder. Including /swagger/swagger.json in the localhost reference was the only way I could get this to work and I think mentioning this for other students may be helpful.

The window that popped up after running benchmark.sh closed immediately after openning. I checked the application insights dashboard and confirmed that the endpoint was being tested. The only way I could get the apache benchmark to show me results was to run the command in my terminal outside of the .sh file. This may be helpful to other students who encounter this issue.

## Future Improvements

To improve this experiment I would allow for deep learning to be enable on the classification model and give it more time to come up with a model with greater accuracy. Another improvement I would make is to see if there is any difference between the programmatic way of building the pipeline and the GUI way of building the pipeline in terms of speed of development and accuracy of the model that gets produced. The last improvement I would make is to see what the response time differences in Apache Benchmark are when manually creating an inference cluster with more resources available. If the response times were significantly improved I would then try to optimize for cost.
