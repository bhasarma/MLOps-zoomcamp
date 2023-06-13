# Deploying your workflow

Today we'll talk about deploying our workflow. Last time we saw, how we can take a notebook, turn it into a script and add some prefect task and flow decorators to make it more observable and resilient. 

Now we'll take the next step in productionizing our workflow and make a deployment that will live on a prefect server running locally. It will allow us to do things like scheduling, future collaboration with other folks e.g. if we are using prefect cloud. This will really help us bringing our deployment to the next level. 

Let's make a deployment using a `Prefect project`. This product is really nice, if we are using something like github like many people. 
If we type:
```
(base) bsarma@turing:~/git-repos/MLOps-zoomcamp$ git remote -v
```

we get:
```
(base) bsarma@turing:~/git-repos/MLOps-zoomcamp$ git remote -v
origin  https://github.com/bhasarma/MLOps-zoomcamp.git (fetch)
origin  https://github.com/bhasarma/MLOps-zoomcamp.git (push)
```

Then, 
```
(prefect-ops) bsarma@turing:~/git-repos/MLOps-zoomcamp/wk-04_module-03_Orchestration-and-ML-pipelines$ prefect project init
Created project in /home/bsarma/git-repos/MLOps-zoomcamp/wk-04_module-03_Orchestration-and-ML-pipelines with the following new files:
.prefectignore
.prefect/
```

- `prefect project init` will create four things:
    - `.prefectignorefile` not something we use right now.
    - `deployment.yaml` . This is useful for templating, if we are doing multiple deployments for one project. We don't need that right now. 
    - `prefect.yaml` we are going to look at it now. 
    - `.prefect` is a hidden folder useful for little bit of short-hand convenience. We don't need it right now.

Keep in mind that if we run `prefect project init`, it willn't overwrite these files. We have to delete them first.

![https://imgur.com/YDHTEQ0](https://imgur.com/YDHTEQ0)

- `prefect deploy --help` for getting help information

Deployment with:
```
(prefect-ops) bsarma@turing:~/git-repos/MLOps-zoomcamp/wk-04_module-03_Orchestration-and-ML-pipelines$ prefect deploy 3.4/orchestrate.py:main_flow -n taxi1 -p zoompool
Deployment 'main-flow/taxi1' successfully created with id 'edfa7662-6ef6-4f62-9d89-ecbd710b0cbc'.
View Deployment in UI: http://127.0.0.1:4200/deployments/deployment/edfa7662-6ef6-4f62-9d89-ecbd710b0cbc

To execute flow runs from this deployment, start a worker that pulls work from the 'zoompool' work pool
```

Then, 
```
(prefect-ops) bsarma@turing:~/git-repos/MLOps-zoomcamp/wk-04_module-03_Orchestration-and-ML-pipelines$ prefect worker start -p zoompool
Discovered worker type 'process' for work pool 'zoompool'.
Worker 'ProcessWorker d28f15ce-729c-489d-8786-abc648398dae' started!
```

Reference:

- link to video: https://www.youtube.com/watch?v=3YjagezFhOo&list=PL3MmuxUbc_hIUISrluw_A7wDSmfOhErJK&index=19

