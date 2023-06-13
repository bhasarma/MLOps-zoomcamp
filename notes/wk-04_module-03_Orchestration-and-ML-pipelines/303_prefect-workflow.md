# Prefect Workflow

In this module we are working on **productionizing our pipelines**. 

We start from `duration-prediction.ipynb` from module 2. This file is available in the folder `3.3` of the repo. This module helps us to train some model and make some predicitons. We'll trun this notebook into a python script, that can be run in a nice repeatable way. We'll use add some Prefect functinalities to make our pipeline more observable and resilient. `orchestrate_pre_prefect.py` is the python script from this notebook. 

We run it with `(prefect-ops) bsarma@turing:~/git-repos/MLOps-zoomcamp/wk-04_module-03_Orchestration-and-ML-pipelines/prefect-mlops-zoomcamp$ python 3.3/orchestrate_pre_prefect.py`. After running successfully we see in the folder that some information from `mlflow` is generated and saved in `mlruns` and also the folder `models`.

To add some observability and orchestration with prefect, so that we get good insght into what really happens of our model, fails to do something, how it is doing when we collaborate with folks, we'll some add some prefect functionalities to the script. We first import `task` and  `flow` decorator with `from prefect import flow, task`. 

In this video, we saw how to use prefect to get little more insight and orchestration possibilities. We also saw how we are moving more to a production environement moving awy from exploration environment i.e. with notebook. In our next video, we'll move even to a more productionized environment with deployments that can be used more reliably and with other folks. 


References: 
- Link to Youtube video: https://www.youtube.com/watch?v=x3bV8yMKjtc&list=PL3MmuxUbc_hIUISrluw_A7wDSmfOhErJK&index=18