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



References:

* Link to video: https://www.youtube.com/watch?v=rTUBTvXvXvM&list=PL3MmuxUbc_hIUISrluw_A7wDSmfOhErJK&index=17

