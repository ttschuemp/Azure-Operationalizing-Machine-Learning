# Building an end-to-end training and deployment solution for MLOps 

This project is centered on a dataset that documents the results of marketing campaigns carried out by a banking institution. These campaigns primarily involved phone calls during which customers were approached to consider subscribing to a bank term deposit. The objective is to utilize customer attributes like age, occupation, education, default status, and balance to forecast whether a customer will ultimately opt for the term deposit. To achieve this, a classification task is performed using Azure Auto ML, and the best performing model is deployed. Once deployed, the model becomes accessible for consumption (REST endpoint). Additionally, an Azure pipeline is designed, published, and made available for consumption as well.

## Architectural Diagram
The project is built to include a simple training pipeline based on a registered dataset in Azure-ML. The best model of a successful run is then deployed as a ACI with logging through Application insights. The pipeline can be triggered through an endpoint or Azure ML directly. <img width="613" alt="Screenshot 2023-10-09 at 18 21 09" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/5e92b390-78de-4cca-b5c7-8c914e7d1f1f">

## Key Steps

Upload the Bank Marketing dataset and make it available: 
<img width="1487" alt="Screenshot 2023-10-09 at 10 48 54" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/615301af-9bb6-461f-b0be-226c04aeb5b5">

Create a training pipeline with AutoML: 

<img width="1188" alt="Screenshot 2023-10-09 at 18 25 32" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/9de1b4c4-3a42-47f4-8ea6-49c3b971cc4a">

Check in the details for the best performing model. You can check many metrics like AOC or accuracy of the model. 
<img width="2131" alt="Screenshot 2023-10-09 at 18 26 29" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/eb16ab7d-b9e3-4034-9482-1b5a7e9927a0">


The best model was considered with an Accuracy of 91.5%: 
<img width="1492" alt="Screenshot 2023-10-09 at 14 25 02" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/51618e1d-7317-4ae8-91b1-b7212c77c602">

And released as a webservice based endpoint with Application Insights activated for logging purposes. Important that the deployment is healthy and make sure to enable the application insights when deploying such that later on logs can be checked. The endpoint can be tested in the Test menu.
<img width="1791" alt="Screenshot 2023-10-09 at 18 30 38" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/4df15bfd-1f7a-4d8e-974d-7a3fe1ad22b7">

This is another way to test the endpoint with the custom python script. We can see that the endpoint/model returns `Yes` and `No` as a result which is what we expected from the exercise: 
<img width="1078" alt="Screenshot 2023-10-09 at 17 45 12" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/4dc43770-1854-439c-8cfc-8877c50bd340">

The application logs can be checked by running the log.py file or also in the azure ML studio directly:
<img width="1717" alt="Screenshot 2023-10-09 at 16 27 32" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/8d657aeb-bfe2-409e-b1e3-3e0de6353a5e">
This is very handy when checking for any errors or bugs while the application is running in production.  
<img width="1756" alt="Screenshot 2023-10-09 at 16 27 59" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/84ea38e8-8e8a-49dd-9036-33aead060b01">

The training pipeline was registered and an endpoint created to allow for remotely or automatically triggering the training pipeline: 

<img width="1573" alt="Screenshot 2023-10-09 at 18 35 28" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/6bbccdcb-aa91-486b-9dbc-ab799ef07798">
The pipeline endpoint shows the training pipeline: 
<img width="1517" alt="Screenshot 2023-10-09 at 18 33 43" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/80b69cfb-3659-4d2a-9f95-def38b39f3f4">
In the Published Pipeline overview section you can see if the pipelien is active. Status of the public pipeline is active: 
<img width="1529" alt="Screenshot 2023-10-10 at 14 04 18" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/3442ae29-b103-4e4e-8ee0-fa773b9bc7e7">



Swagger is used for testing an API but also for documenting and visualizing it. Swagger is a tool that helps you design, document, and interact with REST APIs. It provides a user-friendly interface for developers, allowing them to. We used Swagger to also test our endpoint, running on localhost here:

<img width="1559" alt="Screenshot 2023-10-09 at 17 22 35" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/579e40d1-c903-4c7b-9a89-3068d4fb3d29">
Here also the input data gets visualized by swagger which helps to explain how the API works: 
<img width="1569" alt="Screenshot 2023-10-09 at 17 25 12" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/816a972e-fc58-45cf-8975-e852d7426b76">

To view the progress of the model you can check the run details: 
(Note that the ouput of the RunDetails function is not properly rendering in VS Code. Progress can also be checked on the Details Page)
<img width="1840" alt="Screenshot 2023-10-10 at 18 09 57" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/e79f9ec8-5a0d-4c24-9fa8-92bc5a5550c3">



## Screen Recording
https://youtu.be/DSi1iSVxZBw


## Future development and improvements

Due to the dataset's imbalance, we can use metrics like Weighted-AUC and F1-Score to evaluate models. If they don't meet expectations, we can try Undersampling, Oversampling with SMOTE.

Another approach is tuning hyperparameters for the Voting-Ensemble model from AutoML. This means optimizing the estimators list, voting method (hard or soft), and class label/probability weights for better model performance.
