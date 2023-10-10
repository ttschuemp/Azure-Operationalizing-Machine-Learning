# Building an end-to-end training and deployment solution for MLOps 

This project is centered on a dataset that documents the results of marketing campaigns carried out by a banking institution. These campaigns primarily involved phone calls during which customers were approached to consider subscribing to a bank term deposit. The objective is to utilize customer attributes like age, occupation, education, default status, and balance to forecast whether a customer will ultimately opt for the term deposit. To achieve this, a classification task is performed using Azure Auto ML, and the best performing model is deployed. Once deployed, the model becomes accessible for consumption. Additionally, an Azure pipeline is designed, published, and made available for consumption as well.

## Architectural Diagram
The project is built to include a simple training pipeline based on a registered dataset in Azure-ML. The best model of a successful run is then deployed as a ACI with logging through Application insights. The pipeline can be triggered through an endpoint or Azure ML directly. <img width="613" alt="Screenshot 2023-10-09 at 18 21 09" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/5e92b390-78de-4cca-b5c7-8c914e7d1f1f">

## Key Steps

Upload the Bank Marketing dataset and make it available: 
<img width="1487" alt="Screenshot 2023-10-09 at 10 48 54" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/615301af-9bb6-461f-b0be-226c04aeb5b5">

Create a training pipeline with AutoML: 

<img width="1188" alt="Screenshot 2023-10-09 at 18 25 32" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/9de1b4c4-3a42-47f4-8ea6-49c3b971cc4a">
<img width="2131" alt="Screenshot 2023-10-09 at 18 26 29" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/eb16ab7d-b9e3-4034-9482-1b5a7e9927a0">


The best model was considered: 
<img width="1492" alt="Screenshot 2023-10-09 at 14 25 02" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/51618e1d-7317-4ae8-91b1-b7212c77c602">

And released as a webservice based endpoint with Application Insights activated for logging purposes: 
<img width="1791" alt="Screenshot 2023-10-09 at 18 30 38" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/4df15bfd-1f7a-4d8e-974d-7a3fe1ad22b7">

Test endpoint with python file: 
<img width="1078" alt="Screenshot 2023-10-09 at 17 45 12" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/4dc43770-1854-439c-8cfc-8877c50bd340">

Checking logs: 
<img width="1717" alt="Screenshot 2023-10-09 at 16 27 32" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/8d657aeb-bfe2-409e-b1e3-3e0de6353a5e">
<img width="1756" alt="Screenshot 2023-10-09 at 16 27 59" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/84ea38e8-8e8a-49dd-9036-33aead060b01">

The training pipeline was registered and an endpoint created to allow for remotely or automatically triggering the training pipeline: 

<img width="1573" alt="Screenshot 2023-10-09 at 18 35 28" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/6bbccdcb-aa91-486b-9dbc-ab799ef07798">
<img width="1517" alt="Screenshot 2023-10-09 at 18 33 43" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/80b69cfb-3659-4d2a-9f95-def38b39f3f4">
<img width="1881" alt="Screenshot 2023-10-09 at 18 38 42" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/96c9bcb4-6bc6-4803-9290-c325f296b9c0">

Swagger is running on localhost:

<img width="1559" alt="Screenshot 2023-10-09 at 17 22 35" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/579e40d1-c903-4c7b-9a89-3068d4fb3d29">
<img width="1569" alt="Screenshot 2023-10-09 at 17 25 12" src="https://github.com/ttschuemp/Azure-Operationalizing-Machine-Learning/assets/46277840/816a972e-fc58-45cf-8975-e852d7426b76">

## Screen Recording
https://youtu.be/DSi1iSVxZBw


## Future development and improvements

Due to the dataset's imbalance, we can use metrics like Weighted-AUC and F1-Score to evaluate models. If they don't meet expectations, we can try Undersampling, Oversampling with SMOTE.

Another approach is tuning hyperparameters for the Voting-Ensemble model from AutoML. This means optimizing the estimators list, voting method (hard or soft), and class label/probability weights for better model performance.
