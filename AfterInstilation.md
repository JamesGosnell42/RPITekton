-get the tekton CLI by finding the [CLT release](https://github.com/tektoncd/cli/releases) that is compatible with your system and then entering these two comands 
`curl -LO LINK-TO-THE-PACKAGE`
`sudo dpkg -i ./PACKAGE-NAME`

-run this command in the pipelines directory in your CLI
`kubectl apply --filename \
https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml`

-in th pipelines directory create a yaml named hello-world.yaml containing:
`apiVersion: tekton.dev/v1beta1
kind: Task
metadata:
  name: hello
spec:
  steps:
    - name: echo
      image: alpine
      script: |
        #!/bin/sh
        echo "Hello World"   `
this should result in this
`task.tekton.dev/hello created`

-Run this command to apply it to your pipelines
`kubectl apply --filename hello-world.yaml`

- make a tast run named hello-world-run.yaml containing:
`apiVersion: tekton.dev/v1beta1
kind: TaskRun
metadata:
  name: hello-task-run
spec:
  taskRef:
    name: hello`

- apply with:
`kubectl apply --filename hello-world-run.yaml`

- run with
`kubectl get taskrun hello-task-run`

- check the logs by entering this command:
  `kubectl logs --selector=tekton.dev/taskRun=hello-task-run`

-Create a new file named goodbye-world.yaml and add the following content:
`apiVersion: tekton.dev/v1beta1
kind: Task
metadata:
  name: goodbye
spec:
  params:
  - name: username
    type: string
  steps:
    - name: goodbye
      image: ubuntu
      script: |
        #!/bin/bash
        echo "Goodbye $(params.username)!"`

-Apply the Task file:
`kubectl apply --filename goodbye-world.yaml`

-Create a new file named hello-goodbye-pipeline.yaml and add the following content:
`apiVersion: tekton.dev/v1beta1
kind: Pipeline
metadata:
  name: hello-goodbye
spec:
  params:
  - name: username
    type: string
  tasks:
    - name: hello
      taskRef:
        name: hello
    - name: goodbye
      runAfter:
        - hello
      taskRef:
        name: goodbye
      params:
      - name: username
        value: $(params.username)`

-Apply the Pipeline configuration to your cluster:
`kubectl apply --filename hello-goodbye-pipeline.yaml`

-Make a pipeline run with named hello-goodbye-pipeline-run.yaml containing:
`apiVersion: tekton.dev/v1beta1
kind: PipelineRun
metadata:
  name: hello-goodbye-run
spec:
  pipelineRef:
    name: hello-goodbye
  params:
  - name: username
    value: "Tekton"`

-Start the Pipeline by applying the PipelineRun configuration to your cluster:
`kubectl apply --filename hello-goodbye-pipeline-run.yaml`

-check the logs with 
`tkn pipelinerun logs hello-goodbye-run -f -n default`





      





