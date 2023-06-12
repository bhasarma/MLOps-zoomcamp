# Introduction to Prefect

In this section, we are going to see how to convert a regular python code into a prefect script. We are going to run our own prefect server locally and run some script against the server.

Goals for this section are:
- Clone github repository
- Setup a conda environment
- Start a Prefect server
- Run a Prefect flow
- Checkout Prefect UI

Terminology:
These are also the basic building blocks of Prefect. 
- **Task**- A discreet unit of work in a Prefect workflow. It can be thought of as regular python functions. They take input, perform work and then produce output. 
- **Flow**- They can also be viewed as python functions. They are responsible for serving as the Container for workflow logic. Flows can be leveraged as parent functions used to call tasks and define state dependencies and data dependencies between tasks.

Tasks done:
- clone the github repo
- setup a conda environment decicated for this module
- start a Prefect server
- Run a prefect flow
- Checkout Prefect UI

Running prefect local server:
* create a folder called MLOps and navigate into it
* clone the github repo with `git clone https://github.com/discdiver/prefect-mlops-zoomcamp.git`
* create new conda environemnt with `conda create -n prefect-ops python=3.9.12`
* once the environement is ready activate it with `conda activate prefect-ops`
* check the python version with `python -V`
* navigate to the folder where `requirement.txt` is located and install the required packages with `pip install -r requirements.txt`
* Start the prefect server with `prefect server start`
* Open a separate terminal to run our script in the prefect server. Make sure conda env is activated and you are in the correct directory.
* Before doing above step, copy the API_URL from previous command, to apply it to prefect configuration, so that we are pointing to the correct API_URL with command `prefect config set PREFECT_API_URL=http://127.0.0.1:4200/api`
* It will show the output `Set 'PREFECT_API_URL' to 'http://127.0.0.1:4200/api'.`
* Run the script with `(prefect-ops) bsarma@turing:~/git-repos/MLOps-zoomcamp/wk-04_module-03_Orchestration-and-ML-pipelines/prefect-mlops-zoomcamp/3.2$ python cat_facts.py`. Once the script finishes running, view the Prefect UI
* Run the next python script with `(prefect-ops) bsarma@turing:~/git-repos/MLOps-zoomcamp/wk-04_module-03_Orchestration-and-ML-pipelines/prefect-mlops-zoomcamp/3.2$ python cat_dog_facts.py`
* Then we get log like this:
```bash
17:26:13.514 | INFO    | prefect.engine - Created flow run 'flawless-wren' for flow 'animal-facts'
17:26:13.661 | INFO    | Flow run 'flawless-wren' - Created subflow run 'voracious-hamster' for flow 'fetch-cat-fact'
17:26:14.580 | INFO    | Flow run 'voracious-hamster' - Finished in state Completed()
17:26:14.659 | INFO    | Flow run 'flawless-wren' - Created subflow run 'merry-dove' for flow 'fetch-dog-fact'
17:26:16.070 | INFO    | Flow run 'merry-dove' - Finished in state Completed()
17:26:16.071 | INFO    | Flow run 'flawless-wren' - 🐱: You check your cats pulse on the inside of the back thigh, where the leg joins to the body. Normal for cats: 110-170 beats per minute.
🐶: Pugs and other dogs with short muzzles have a peculiar head-type known as "Brachycephalic."
17:26:16.110 | INFO    | Flow run 'flawless-wren' - Finished in state Completed('All states completed.')
```

References:

* Link to video: https://www.youtube.com/watch?v=rTUBTvXvXvM&list=PL3MmuxUbc_hIUISrluw_A7wDSmfOhErJK&index=17

