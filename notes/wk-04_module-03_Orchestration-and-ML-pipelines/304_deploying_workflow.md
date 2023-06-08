# Deploying your workflow

key commands used in the lecture:

- `git command -V` : prints the username and repo you are in at the moment
- `prefect project init` will create four things:
    - `.prefectignorefile` not something we use right now.
    - `deployment.yaml` . This is useful for templating, if we are doing multiple deployments for one project. We don't need that right now. 
    - `prefect.yaml` we are going to look at it now. 
    - `.prefect` is a hidden folder

Keep in mind that if we run `prefect project init`, it willn't overwrite these files.  

![](https://imgur.com/YDHTEQ0)

- `prefect deploy --help` for getting help information

Reference:

- link to video: https://www.youtube.com/watch?v=3YjagezFhOo&list=PL3MmuxUbc_hIUISrluw_A7wDSmfOhErJK&index=19

