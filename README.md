# Building an end-to-end training and deployment solution for MLOps 

This project is centered on a dataset that documents the results of marketing campaigns carried out by a banking institution. These campaigns primarily involved phone calls during which customers were approached to consider subscribing to a bank term deposit. The objective is to utilize customer attributes like age, occupation, education, default status, and balance to forecast whether a customer will ultimately opt for the term deposit. To achieve this, a classification task is performed using Azure Auto ML, and the best performing model is deployed. Once deployed, the model becomes accessible for consumption. Additionally, an Azure pipeline is designed, published, and made available for consumption as well.

## Architectural Diagram
The project is built to include a simple training pipeline based on a registered dataset in Azure ML. The best model of a successful run is then deployed as a Azure container instance with logging through Application insights. The pipeline can be triggered through an endpoint or Azure ML directly. 
![image info](./screenshots/architecture.png)
## Key Steps
While all steps have been done programmatically, they are represented here often through the UI.

First we registered the relevant dataset. Please note that the data set was registered twice once through the UI but due to wrong name, it was registered under the correct name throught the script.
![image info](./screenshots/registered_dataset.PNG)

The dataset was then combined with an AutoML step to create a training pipeline creating models based on the dataset.
![image info](./screenshots/pipeline.PNG)

Then a run was triggered of the pipeline that completed successfully
![image info](./screenshots/completed_experiment.PNG)

The best model from the automl run was registered ...
![image info](./screenshots/Best_model.PNG)

And released as a webservice based endpoint with Application Insights activated for logging purposes (please not that the screenshot was taken during transition phase which is why some values are not available).
![image info](./screenshots/insights_enabled.PNG)

The model endpoint on deployment completion was asked through a python notebook to make test forecast and returned the expected results. 
![image info](./screenshots/endpoint_code.PNG)
![image info](./screenshots/endpoint_output.PNG)

The logs could be easily checked through a separate python script.
![image info](./screenshots/logs_output.PNG)

More information for the endpoint was generated using swagger.
![image info](./screenshots/swagger.PNG)

The training pipeline was registered and an endpoint created to allow for remotely or automatically triggering the training pipeline.
![image info](./screenshots/pipeline.PNG)
![image info](./screenshots/endpoint.PNG)

In the python notebook the details of the triggered pipeline runs can be checked and we see, everythign worked.
![image info](./screenshots/Notebook.PNG)

! Please note: Due to the virtual machine crashing, there are screenshots from 2 different implementations and thus names will not always match in the screenshots.

## Screen Recording
https://youtu.be/xawKrqBMtSw

## Standout Suggestions
Unfortunately due to the VM crash there was little time to do standout suggestions but some experiments with coding in different pipeline steps were explored.

## Future development and improvements
- Working with different steps in the ML pipeline such as feature engineering, parallelisation
- Add model registration and release to pipeline
