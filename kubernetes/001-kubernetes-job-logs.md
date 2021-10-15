---
id: 001-kubernetes-job-logs.md
title: Show Kubernetes Job Logs
tags: 
    - kubernetes
    - kubectl
    - kubernetes-job
    - logs
    - cli
date: 2020-10-13 17:50:14 +0200 
keywords: kubernetes, job, logs, read logs
categories: 
    - kubernetes
cover: ../../images/kubernetes.png
author: Pavle Jonoski
meta-description: Read logs of a kubernetes job
---

# Get Kubernetes Job Logs

When using [Kubernetes](https://kubernetes.io/), often you need to read logs from the running pods.
On a bigger cluster you may have many pods that are running and many that have either completed or errored out.
When deploying [Kubernetes Jobs](https://kubernetes.io/docs/concepts/workloads/controllers/job/), often you want to read the logs of the job, whether it completed or has any errors.
Finding the correct pod amongst many pods may be a bit of a challenge.

In this post you'll learn how to list the correct job pods - all of them, and how to retrieve the job logs - from the current 
completed pod and from a pods that exited with error.

Given you already have a Kubernetes cluster, and the job was deployed in a namespace, this is what you want to do.

## List the job pods
Let's say we have a job like this:

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: calculate-fibonacci
  namespace: example
spec:
  template:
    spec:
      containers:
      - name: fibonacci
        image: node:16-alpine
        command: ['node',  '-e', 'function f(x){ if(x === 1 || x === 2) return 1; return f(x-1)+f(x-2);} console.log("The 10th fibonacci number is: ", f(10));']
      restartPolicy: Never
  backoffLimit: 4
```

The Job definition:
 * The name of the job is `calculate-fibonacci`
 * The job is in namespace called `example`


To list the pods associated with this job, do:

```bash
kubectl -n example get pods -l job-name=calculate-fibonacci
```

* `-n example` - this tells `kubectl` to work in the `example` namespace
* `get pods` will give us the list of pods in the namespace
* `-l job-name=calculate-fibonacci` this refines the list of pods that have a label `job-name` with the name of our job: `calculate-fibonacci`

This will produce the following output:
```
NAME                           READY   STATUS      RESTARTS   AGE
calculate-fibonacci--1-pdzg4   0/1     Completed   0          3s
```

## Get the job logs

Once we know the pods associated with a job, we can view the logs the same way we view the logs for any pod: `kubectl logs <the id of the pod>`:

```bash
kubectl -n example logs calculate-fibonacci--1-pdzg4
```

It will give us the logs for the job:

```
The 10th fibonacci number is:  55
```

If the job is still running and we want to follow the logs as they are printed out, just add `-f` (follow) to the command:

```bash
kubectl -n example logs -f calculate-fibonacci--1-pdzg4
```
## One-liner for viewing the logs of a completed job

Now we can combine the both commands into a single one, to view the logs for a completed job:

```bash
kubectl -n example logs $(kubectl -n example get pods -l job-name=calculate-fibonacci --field-selector='status.phase=Succeeded' --no-headers -o custom-columns=':metadata.name')
```

It will give us the logs of the completed pod directly:

```
The 10th fibonacci number is:  55
```

Notice that we added a couple of things in the command that selects the pod:
* `--field-selector='status.phase=Succeeded'` - we want to find the pod that has `Succeeded` status (everything went OK)
* `--no-headers` - we don't want any headers in the output, as we only want the pod id
* `custom-columns=':metadata.name'` - show just the `metadata.name` of the pod (the id)
