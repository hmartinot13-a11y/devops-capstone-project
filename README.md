# Description of the devops-capstone-project. 
Capstone Overview
In this Capstone project, you will apply many of the technologies and concepts you learned in the preceding courses to build and deliver a fully functional Customer Accounts microservice.

Starting in Module 1, you will begin this capstone journey by developing an Agile plan to build your RESTful microservice. You will create a GitHub repository and Kanban board to manage the project, build a user story template to write well-structured user stories, and populate your Product Backlog with all the stories needed to implement the Customer Accounts microservice. After completing your backlog, you will prepare a sprint plan by setting up sprints, estimating story points, assigning stories to the appropriate sprint, and building your Sprint Backlog. Throughout the Capstone, you will take screenshots and record GitHub URLs as evidence for final submission.

In Module 2, you will begin Sprint 1 by configuring your project environment and developing the Customer Accounts microservice using test-driven development (TDD). As you work on each story, you will move it across your Kanban board—from “Backlog” to “In Progress,” then to “Done,” and ultimately to “Closed.”
You will create a development branch for your sprint work and push changes to GitHub by submitting pull requests. You will write test cases for the read, update, delete, and list functions for your RESTful Flask service and write just enough code to make each test pass. You will run nosetests to ensure all tests pass and use the coverage tool to maintain at least 95% test coverage.

In Module 3, you will move into Sprint 2, where you will configure a GitHub Actions continuous integration (CI) workflow that runs automatically whenever a pull request or push is made to the main branch. As part of Sprint 2, you will build a workflow that performs linting with Flake8, runs your tests, checks code coverage, and validates code quality.
You will then enhance your microservice by adding secure coding practices. This includes adding Flask-Talisman for security headers and Flask-CORS to establish Cross-Origin Resource Sharing policies. Following TDD, you will write failing tests, implement the required security features, ensure the tests pass, and merge your work into the main branch.

In Module 4, you will begin Sprint 3, where you will work on deployment-related user stories. You will create a Dockerfile, build a Docker image for the Customer Accounts service, and push the image to the IBM Cloud Container Registry. You will manually deploy your application to an OpenShift/Kubernetes cluster. You will also create a PostgreSQL service in OpenShift and write the Kubernetes deployment and service YAML manifests required to deploy your microservice. As with earlier sprints, you will commit, push, and merge your changes as you progress through each story.

In Module 5, you will extend your deployment work by creating a Tekton continuous delivery (CD) pipeline to automate the deployment of your microservice to Kubernetes. When triggered, this pipeline will clone your repository, lint and test your code, build your Docker image, and deploy the updated service to the cluster without manual intervention.

In Module 6, you will collect and organize all required evidence—screenshots, URLs, and outputs—from the hands-on labs for submission. Your work will be evaluated using Option 1: AI-Graded Submission and Evaluation or Option 2: Peer-Graded Submission and Evaluation.

Finally, in Module 7, you will complete the Final Exam to validate your understanding of the DevOps concepts and practices applied throughout the Capstone project.

# DevOps Capstone Template

[![Build Status](https://github.com/hmartinot13-a11y/devops-capstone-project/actions/workflows/ci-build.yaml/badge.svg)]
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python 3.9](https://img.shields.io/badge/Python-3.9-green.svg)](https://shields.io/)

This repository contains the starter code for the project in [**IBM-CD0285EN-SkillsNetwork DevOps Capstone Project**](https://www.coursera.org/learn/devops-capstone-project?specialization=devops-and-software-engineering) which is part of the [**IBM DevOps and Software Engineering Professional Certificate**](https://www.coursera.org/professional-certificates/devops-and-software-engineering)

## Usage

You should use this template to start your DevOps Capstone project. It contains all of the code that you will need to get started.

Do Not fork this code! It is meant to be used by pressing the  <span style=color:white;background:green>**Use this Template**</span> button in GitHub. This will copy the code to your own repository with no connection back to the original repository like a fork would. This is what you want.

## Development Environment

These labs are designed to be executed in the IBM Developer Skills Network Cloud IDE with OpenShift. Please use the links provided in the Coursera Capstone project to access the lab environment.

Once you are in the lab environment, you can initialize it with `bin/setup.sh` by sourcing it. (*Note: DO NOT run this program as a bash script. It sets environment variable and so must be sourced*):

```bash
source bin/setup.sh
```

This will install Python 3.9, make it the default, modify the bash prompt, create a Python virtual environment and activate it.

After sourcing it you prompt should look like this:

```bash
(venv) theia:project$
```

## Useful commands

Under normal circumstances you should not have to run these commands. They are performed automatically at setup but may be useful when things go wrong:

### Activate the Python 3.9 virtual environment

You can activate the Python 3.9 environment with:

```bash
source ~/venv/bin/activate
```

### Installing Python dependencies

These dependencies are installed as part of the setup process but should you need to install them again, first make sure that the Python 3.9 virtual environment is activated and then use the `make install` command:

```bash
make install
```

### Starting the Postgres Docker container

The labs use Postgres running in a Docker container. If for some reason the service is not available you can start it with:

```bash
make db
```

You can use the `docker ps` command to make sure that postgres is up and running.

## Project layout

The code for the microservice is contained in the `service` package. All of the test are in the `tests` folder. The code follows the **Model-View-Controller** pattern with all of the database code and business logic in the model (`models.py`), and all of the RESTful routing on the controller (`routes.py`).

```text
├── service         <- microservice package
│   ├── common/     <- common log and error handlers
│   ├── config.py   <- Flask configuration object
│   ├── models.py   <- code for the persistent model
│   └── routes.py   <- code for the REST API routes
├── setup.cfg       <- tools setup config
└── tests                       <- folder for all of the tests
    ├── factories.py            <- test factories
    ├── test_cli_commands.py    <- CLI tests
    ├── test_models.py          <- model unit tests
    └── test_routes.py          <- route unit tests
```

## Data Model

The Account model contains the following fields:

| Name | Type | Optional |
|------|------|----------|
| id | Integer| False |
| name | String(64) | False |
| email | String(64) | False |
| address | String(256) | False |
| phone_number | String(32) | True |
| date_joined | Date | False |

## Your Task

Complete this microservice by implementing REST API's for `READ`, `UPDATE`, `DELETE`, and `LIST` while maintaining **95%** code coverage. In true **Test Driven Development** fashion, first write tests for the code you "wish you had", and then write the code to make them pass.

## Local Kubernetes Development

This repo can also be used for local Kubernetes development. It is not advised that you run these commands in the Cloud IDE environment. The purpose of these commands are to simulate the Cloud IDE environment locally on your computer. 

At a minimum, you will need [Docker Desktop](https://www.docker.com/products/docker-desktop) installed on your computer. For the full development environment, you will also need [Visual Studio Code](https://code.visualstudio.com) with the [Remote Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension from the Visual Studio Marketplace. All of these can be installed manually by clicking on the links above or you can use a package manager like **Homebrew** on Mac of **Chocolatey** on Windows.

Please only use these commands for working stand-alone on your own computer with the VSCode Remote Container environment provided.

1. Bring up a local K3D Kubernetes cluster

    ```bash
    $ make cluster
    ```

2. Install Tekton

    ```bash
    $ make tekton
    ```

3. Install the ClusterTasks that the Cloud IDE has

    ```bash
    $ make clustertasks
    ```

You can now perform Tekton development locally, just like in the Cloud IDE lab environment.

## Author

[John Rofrano](https://www.coursera.org/instructor/johnrofrano), Senior Technical Staff Member, DevOps Champion, @ IBM Research, and Instructor @ Coursera

## License

Licensed under the Apache License. See [LICENSE](LICENSE)

## <h3 align="center"> © IBM Corporation 2022. All rights reserved. <h3/>
