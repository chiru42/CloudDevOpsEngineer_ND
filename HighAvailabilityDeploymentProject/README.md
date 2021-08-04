# Project: Deploy a High-Availability Web App using CloudFormation
This directory contains the project submission artefacts for the Cloud DevOps Nanodegree program.

## CloudFormation Diagram
![alt text](https://github.com/chiru42/CloudDevOpsEngineer_ND/blob/chiru42-patch-1/HighAvailabilityDeploymentProject/UdagramDiagram.jpeg)

## Input package for deployment
Download udagram project: s3://udagramproj/udagramPackage.zip

*P.S: The zip file contains blank file demo.html*

## Project Architecture
---
The project contains below 2 stacks:

**ourdemoinfra.yaml**: which holds the project infrastructure layer such as (VPC, Subnets, Gateways and Routes)

**udagramServers.yaml**: which holds the project application layer such as (instance launch condfigurations, Autoscaling)

## Setting up Stacks in AWS
---
The sequence for stack creation is as mentioned below
1. aws cloudformation create-stack --stack-name udagramInfra --template-body ourinfra.yaml --parameters ourinfra-parameters.json 
2. aws cloudformation create-stack --stack-name udagramApp --template-body file://udagramServers.yaml  --parameters file://udagramServers-parameters.json --region=us-east-1 --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM"


![aws screenshot](https://github.com/chiru42/CloudDevOpsEngineer_ND/blob/chiru42-patch-1/HighAvailabilityDeploymentProject/stack_setup.PNG)


## Deletion of CloudFormation Stacks
---
The sequence for stack deletion is a mentioned below
1. aws cloudformation delete-stack --stack-name udagramApp
2. aws cloudformation delete-stack --stack-name udagramInfra

## Udagram Access Link
---
[http://udagr-webap-18tbo0bqm32vh-1337185447.us-east-1.elb.amazonaws.com](http://udagr-webap-18tbo0bqm32vh-1337185447.us-east-1.elb.amazonaws.com)

### Screenshot of successful server launch via Load Balancer DNS name
![server screenshot](https://github.com/chiru42/CloudDevOpsEngineer_ND/blob/main/HighAvailabilityDeploymentProject/serverhtml.PNG)
