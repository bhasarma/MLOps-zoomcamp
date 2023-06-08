# Module 3: Orchestration and ML Pipelines

Here we'll learn how to use the tool **Prefect** for ML orchestration and make sure our ML pipeline is resilient.

In this introductory video, we'll talk about **Workflow Orchestration**, what it is and how **Prefect** can help to solve some needs. 

A typical MLOPs workflow could start with some python code to fetch the data, preprocessing this data, some pandas code, then scikit learn to train, xgboost for some training, then mlflow to track everything and finally model is being served with Flask. We can failure points at each of these steps. If you code for very long, often things break. 

Prefect allows us to Orchestrate and Observe our python workflows at scale.

Goal of this modeule is to learn how to use Prefect to orchestrate and observe your ML workflows.


References: 

* Link to the video: https://www.youtube.com/watch?v=Cqb7wyaNF08&list=PL3MmuxUbc_hIUISrluw_A7wDSmfOhErJK&index=16