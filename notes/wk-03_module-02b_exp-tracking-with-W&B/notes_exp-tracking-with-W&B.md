# Experiment tracking with Weights & Biases

## What is Weights & Biases?

W&B is an MLOps platform. Experiment tracking is one of the many offerings it provides. If you sign up into W&B, you get access to experiment tracking, artifacts (for Datasets and model versioning), tables (interactive data visualizations, collaborative dashboards), hyperparameter optimization, Automate ML workflows and many mores.

W&B is basically integrated with almost all open source frameworks and libraries. 

## What is an ML experiment? And,

## Why track an experiment?

In ML we need to do lots of trials and errors, to get the best hyperparameter or model. Machine learning is highly empirical. 

We track an experiment for 3 major reasons: 
- share results
- take business decisions
- reproducibility

## Tracking experiments traditionally

- using log files, then parsing these log files using regular expressions into spread sheet. Then sometime later came the tool TensorBoard. One major problem with TensorBoard was that it is little difficult to scale, if you are not creating your own Tensorboard hosting service. It is also difficult to compare 2 diffierent TensorBoard experiments together, making it difficult to share results with others. It doesn't scale at all well, as the number of people you are collaborating with increases. 

## A system of record for all ML Workflows

What is all of these done by one web application. W&B can be considfered as a system of record for all workflows. 

Philosophy of W&B revolves wround two concepts, One is run, which is equivalent to an experiment. 

Paradigm - it is a run (basically an experiment). You start an experiment by calling `wandb.init()`. `wandb` is the python client library for W&B. Once you have initiliazed an experiment, you log something to W&B using `wandb.log(metrics)`. Metrics can be training and validation losses, your errors, accuracy, model checkpoint files, version directories, artefacts, media rich dataframes and a lot more.

## Time for a demo

We saw how to log some information into W&B

## Asking questions about your data and model 

We do it usually by writing sql queries or with pandas. By writing lots of codes. We use lots of operations like split, combine, groupby etc. 

## Interactive Dataframes with Rich Media Support 

`wandb.table`

## Unified reporting and dashboarding

It is a way to share your result and publish your ML result using a tool called reports. 

Let's see how we can create a report. 
