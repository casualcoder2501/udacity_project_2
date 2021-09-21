# Udacity Project 2: Pipelines and Deployment

This objective of this project was to learn how to use Azure ML Studio to deploy and consume both autoML pipelines and stand-alone models. Swagger and Apache Benchmark were other technologies that were utilized for this project to both aid in documentation of the endpoint and testing the endpoint's capabilities in responding to user requests respectively.

## Architectural Diagram
![image](https://user-images.githubusercontent.com/28558135/134101936-648893b2-fc82-4845-b00d-6f6849583a2e.png)

## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screenshots required to demonstrate key steps.
### Created a Service Principle
<img width="725" alt="azure-az-auth" src="https://user-images.githubusercontent.com/28558135/134102097-3caf1210-9a0c-40e6-8ba7-ac52741468f3.png">
Using the az commandline tool I created an SP for Azure ML
### Workspace Share
<img width="633" alt="azure-ml-workspace-share" src="https://user-images.githubusercontent.com/28558135/134102268-dce6a1c7-79b7-4c95-b42d-8d9f8015c1d5.png">
Using the workspace share command I assigned the previously created SP to the role of admin
### Dataset Registration
<img width="2032" alt="banking_data_registered" src="https://user-images.githubusercontent.com/28558135/134102392-ae86d79b-ea0d-40e2-ac73-423ab567a293.png">
The banking data was registered as a dataset prior to running the AutoML experiment
## Screen Recording
https://youtu.be/_WSIqnUVAlc

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
