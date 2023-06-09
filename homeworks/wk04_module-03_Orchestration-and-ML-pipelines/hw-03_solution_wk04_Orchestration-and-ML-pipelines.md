## Solution to Homework 04 | WEEK 04 | Module 03 | Orchestration and ML Pipelines with Prefect

![Prefect logo](./images/prefect-logo.svg)

---

You can find the questions for this homework here [here](https://github.com/DataTalksClub/mlops-zoomcamp/blob/main/cohorts/2023/03-orchestration/homework.md)

The goal of this homework is to familiarize users with workflow orchestration using Prefect. 

Start with the orchestrate.py file in the 03-orchestration/3.4 folder
of the course repo: https://github.com/DataTalksClub/mlops-zoomcamp/blob/main/03-orchestration/3.4/orchestrate.py


## Q1. Human-readable name

You’d like to give the first task, `read_data` a nicely formatted name.
How can you specify a task name?

> Hint: look in the docs at https://docs.prefect.io or 
> check out the doc string in a code editor.

- `@task(retries=3, retry_delay_seconds=2, name="Read taxi data")`
- `@task(retries=3, retry_delay_seconds=2, task_name="Read taxi data")`
- `@task(retries=3, retry_delay_seconds=2, task-name="Read taxi data")`
- `@task(retries=3, retry_delay_seconds=2, task_name_function=lambda x: f"Read taxi data")`

**Answer to Q1**

`@task(retries=3, retry_delay_seconds=2, name="Read taxi data")`

## Q2. Cron

Cron is a common scheduling specification for workflows. 

Using the flow in `orchestrate.py`, create a deployment.
Schedule your deployment to run on the third day of every month at 9am UTC.
What’s the cron schedule for that?

- `0 9 3 * *`
- `0 0 9 3 *`
- `9 * 3 0 *`
- `* * 9 3 0`

**Answer to Q2**

![Crone scheduler Syntax](./images/crone-schedule-syntax.png)

`0 9 3 * *`

## Q3. RMSE

Download the January 2023 Green Taxi data and use it for your training data.
Download the February 2023 Green Taxi data and use it for your validation data. 

Make sure you upload the data to GitHub so it is available for your deployment.

Create a custom flow run of your deployment from the UI. Choose Custom
Run for the flow and enter the file path as a string on the JSON tab under Parameters.

Make sure you have a worker running and polling the correct work pool.

View the results in the UI.

What’s the final RMSE to five decimal places?

- 6.67433
- 5.19931
- 8.89443
- 9.12250

**Answer ro Q3**
- Download January 2023 green taxi data and use it for your training data
```
(base) bsarma@turing:~/git-repos/MLOps-zoomcamp/homeworks/wk04_module-03_Orchestration-and-ML-pipelines/data$ wget https://d37ci6vzurychx.cloudfront.net/trip-data/green_tripdata_2023-01.parquet
--2023-06-14 10:33:28--  https://d37ci6vzurychx.cloudfront.net/trip-data/green_tripdata_2023-01.parquet
Resolving d37ci6vzurychx.cloudfront.net (d37ci6vzurychx.cloudfront.net)... 2600:9000:2156:400:b:20a5:b140:21, 2600:9000:2156:8200:b:20a5:b140:21, 2600:9000:2156:e00:b:20a5:b140:21, ...
Connecting to d37ci6vzurychx.cloudfront.net (d37ci6vzurychx.cloudfront.net)|2600:9000:2156:400:b:20a5:b140:21|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1427002 (1,4M) [binary/octet-stream]
Saving to: ‘green_tripdata_2023-01.parquet’

green_tripdata_2023-01.parquet                 100%[===================================================================================================>]   1,36M  --.-KB/s    in 0,1s    

2023-06-14 10:33:28 (13,4 MB/s) - ‘green_tripdata_2023-01.parquet’ saved [1427002/1427002]
```
- download February 2023 Green Taxi data and use it for validation data

```
(base) bsarma@turing:~/git-repos/MLOps-zoomcamp/homeworks/wk04_module-03_Orchestration-and-ML-pipelines/data$ wget https://d37ci6vzurychx.cloudfront.net/trip-data/green_tripdata_2023-02.parquet
--2023-06-14 10:35:59--  https://d37ci6vzurychx.cloudfront.net/trip-data/green_tripdata_2023-02.parquet
Resolving d37ci6vzurychx.cloudfront.net (d37ci6vzurychx.cloudfront.net)... 2600:9000:2156:7c00:b:20a5:b140:21, 2600:9000:2156:cc00:b:20a5:b140:21, 2600:9000:2156:1800:b:20a5:b140:21, ...
Connecting to d37ci6vzurychx.cloudfront.net (d37ci6vzurychx.cloudfront.net)|2600:9000:2156:7c00:b:20a5:b140:21|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1533740 (1,5M) [binary/octet-stream]
Saving to: ‘green_tripdata_2023-02.parquet’

green_tripdata_2023-02.parquet                 100%[===================================================================================================>]   1,46M  --.-KB/s    in 0,1s    

2023-06-14 10:35:59 (13,2 MB/s) - ‘green_tripdata_2023-02.parquet’ saved [1533740/1533740]
```
Step 3: activate the conda environment \
`(base) bsarma@turing:~/git-repos/MLOps-zoomcamp/homeworks/wk04_module-03_Orchestration-and-ML-pipelines$ conda activate prefect-ops`

Step 4: initialize the project: \
`(prefect-ops) bsarma@turing:~/git-repos/MLOps-zoomcamp/homeworks/wk04_module-03_Orchestration-and-ML-pipelines$ prefect project init`

Step 5: start the server: \
`(prefect-ops) bsarma@turing:~/git-repos/MLOps-zoomcamp/homeworks/wk04_module-03_Orchestration-and-ML-pipelines$ prefect server start`

Step 6: Open the UI in browser with `http://127.0.0.1:4200`

Step 7: Open another terminal, activate the conda env and navigate to where python script for homweok `orchestrate.py` is located

Step 8: deploy the script into the pool called hw-04-pool
```
(prefect-ops) bsarma@turing:~/git-repos/MLOps-zoomcamp/homeworks/wk04_module-03_Orchestration-and-ML-pipelines$  prefect deploy orchestrate.py:main_flow -n green-taxi-23 -p hw-04-pool
Deployment 'main-flow/green-taxi-23' successfully created with id '9d2ccafd-5db9-4e05-aa81-f1546d131e6f'.
View Deployment in UI: http://127.0.0.1:4200/deployments/deployment/9d2ccafd-5db9-4e05-aa81-f1546d131e6f

To execute flow runs from this deployment, start a worker that pulls work from the 'hw-04-pool' work pool
```
Step 9: start a worker that pulls work from the pool
```
(prefect-ops) bsarma@turing:~/git-repos/MLOps-zoomcamp/homeworks/wk04_module-03_Orchestration-and-ML-pipelines$ prefect worker start -p hw-04-pool
Discovered worker type 'process' for work pool 'hw-04-pool'.
Worker 'ProcessWorker d923c790-1c26-4967-9b9e-8abb9aab74a3' started!
```

Step 10: Start another terminal and activate the conda env.

Step 11: Start a run of the deployed flow either from CLI or from the UI

## Q4. RMSE (Markdown Artifact)

Download the February 2023 Green Taxi data and use it for your training data.
Download the March 2023 Green Taxi data and use it for your validation data. 

Create a Prefect Markdown artifact that displays the RMSE for the validation data.
Create a deployment and run it.

What’s the RMSE in the artifact to two decimal places ?

- 9.71
- 12.02
- 15.33
- 5.37


## Q5. Emails


It’s often helpful to be notified when something with your dataflow doesn’t work
as planned. Create an email notification for to use with your own Prefect server instance.
In your virtual environment, install the prefect-email integration with 

```bash
pip install prefect-email
```

Make sure you are connected to a running Prefect server instance through your
Prefect profile.
See the docs if needed: https://docs.prefect.io/latest/concepts/settings/#configuration-profiles

Register the new block with your server with 

```bash
prefect block register -m prefect_email
```

Remember that a block is a Prefect class with a nice UI form interface.
Block objects live on the server and can be created and accessed in your Python code. 

See the docs for how to authenticate by saving your email credentials to
a block and note that you will need an App Password to send emails with
Gmail and other services. Follow the instructions in the docs.

Create and save an `EmailServerCredentials` notification block.
Use the credentials block to send an email.

Test the notification functionality by running a deployment.

What is the name of the pre-built prefect-email task function?

- `send_email_message`
- `email_send_message`
- `send_email`
- `send_message`



## Q6. Prefect Cloud

The hosted Prefect Cloud lets you avoid running your own Prefect server and
has automations that allow you to get notifications when certain events occur
or don’t occur. 

Create a free forever Prefect Cloud account at [app.prefect.cloud](https://app.prefect.cloud/) and connect
your workspace to it following the steps in the UI when you sign up. 

Set up an Automation from the UI that will send yourself an email when
a flow run completes. Run one of your existing deployments and check
your email to see the notification.

Make sure your active profile is pointing toward Prefect Cloud and
make sure you have a worker active.

What is the name of the second step in the Automation creation process?

- Details
- Trigger
- Actions
- The end


## Submit the results

* Submit your results here: https://forms.gle/nVSYH5fGGamdY1LaA
* You can submit your solution multiple times. In this case, only the last submission will be used
* If your answer doesn't match options exactly, select the closest one


## Deadline

The deadline for submitting is 12 June (Monday), 23:00 CEST (Berlin time). 

After that, the form will be closed.
