---
id: 002-Jenkins-Pipeline-CI-CD-Overview.md
title: Jenkins Pipeline Example.
tags:
  - ci
  - jenkins-pipeline
  - jenkins-ci
author: Partha Talukdar
meta-description: Maintaining Continuous Integration Pipelines using Jenkins DSL.
date: 2020-06-21 20:28:46 +0200
keywords: ci, jenkins-ci, jenkins
template: post
categories:
  - ci
cover: ../../images/categories/ci.png
---

# Jenkins Pipeline

Jenkins Pipeline is a continuous delivery (CD) pipeline and has automated expression of processes that enables the code to move from the version control system and through all the processes of testing and deployment, so that the best and reliable built is handed over to your end users and customers.
Pipeline provides an extensible set of tools for modeling simple-to-complex delivery pipelines "as code" via the Pipeline domain-specific language (DSL) syntax.


## Creating a Jenkinsfile and committing it to source control provides a number of immediate benefits:
    
   1.Automatically creates a Pipeline build process for all branches and pull requests.

   2.Code review/iteration on the Pipeline (along with the remaining source code).

   3.Audit trail for the Pipeline.

   4.Single source of truth for the Pipeline, which can be viewed and edited by multiple members of the project.
 
## Why Pipeline?

Pipeline adds a powerful set of automation tools onto Jenkins, supporting use cases that span from simple continuous integration to comprehensive CD pipelines. By modeling a series of related tasks, users can take advantage of the many features of Pipeline:
    
   ```
   1.Code: Pipelines are implemented in code and typically checked into source control, giving teams the ability to edit, review, and iterate upon their delivery pipeline.
   2.Durable: Pipelines can survive both planned and unplanned restarts of the Jenkins controller.
   3.Pausable: Pipelines can optionally stop and wait for human input or approval before continuing the Pipeline run.
   4.Versatile: Pipelines support complex real-world CD requirements, including the ability to fork/join, loop, and perform work in parallel.
   5.Extensible: The Pipeline plugin supports custom extensions to its DSL [1] and multiple options for integration with other plugins.
   ```
## Pipeline concepts

The following concepts are key aspects of Jenkins Pipeline, which tie in closely to Pipeline syntax.

### Pipeline

A Pipeline is a user-defined model of a CD pipeline. A Pipeline’s code defines your entire build process, which typically includes stages for building an application, testing it and then delivering it.

### Node

A node is a machine which is part of the Jenkins environment and is capable of executing a Pipeline.

### Stage

A stage block defines a conceptually distinct subset of tasks performed through the entire Pipeline (e.g. "Build", "Test" and "Deploy" stages), which is used by many plugins to visualize or present Jenkins Pipeline status/progress. [6]

### Step

A single task. Fundamentally, a step tells Jenkins what to do at a particular point in time (or "step" in the process). For example, to execute the shell command make use the sh step: sh 'make'. When a plugin extends the Pipeline DSL, [1] that typically means the plugin has implemented a new step.
Pipeline syntax overview


### Pipeline example

Example of a Jenkinsfile using Declarative Pipeline syntax:

```
pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
            steps { 
                sh 'make' 
            }
        }
        stage('Test'){
            steps {
                sh 'make check'
                junit 'reports/**/*.xml' 
            }
        }
        stage('Deploy') {
            steps {
                sh 'make publish'
            }
        }
    }
}
```
```
1. pipeline is Declarative Pipeline-specific syntax that defines a "block" containing all content and instructions for executing the entire Pipeline.

2. agent is Declarative Pipeline-specific syntax that instructs Jenkins to allocate an executor (on a node) and workspace for the entire Pipeline.

3. stage is a syntax block that describes a stage of this Pipeline. Read more about stage blocks in Declarative Pipeline syntax on the Pipeline syntax page. As mentioned above, stage blocks are optional in Scripted Pipeline syntax.

4. steps is Declarative Pipeline-specific syntax that describes the steps to be run in this stage.

5. sh is a Pipeline step (provided by the Pipeline: Nodes and Processes plugin) that executes the given shell command.

6. junit is another Pipeline step (provided by the JUnit plugin) for aggregating test reports.

7. node is Scripted Pipeline-specific syntax that instructs Jenkins to execute this Pipeline (and any stages contained within it), on any available agent/node. This is effectively equivalent to agent in Declarative Pipeline-specific syntax.


```   

# More On Jenkins Pipeline at:

[Jenkins Pipeline](https://www.jenkins.io/doc/book/pipeline/)

[Pipeline Syntax](https://www.jenkins.io/doc/book/pipeline/syntax)

[Using Jenkinsfile](https://www.jenkins.io/doc/book/pipeline/jenkinsfile/)
