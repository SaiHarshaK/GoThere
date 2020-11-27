# Go There
[![Build Status](http://ec2-54-167-230-179.compute-1.amazonaws.com:8080/buildStatus/icon?job=Concurrency/master)](http://ec2-54-167-230-179.compute-1.amazonaws.com:8080/job/Concurrency/job/master/)

##### We are live at [GoThere](www.gothere.tk)
\
Go There is a dynamic path finding and optimising application. Using parallelism at every step to ensure performance.
Essentially providing a fast approximation to the Travelling Salesman Problem.Given a set of destinations the most
effecient way to visit all of them is provided by it.

## Architecture
We have a two server architecture.
- One server running a private **Jenkins CI**.
- Another one for CD running a **dockerised** version of the application.

On pushes to **master**, jenkins runs tests and builds. If successful an image of the built app is pushed to docker hub.
The deployment server is also triggered which pulls this image from docker hub and runs the latest app live, ensuring CI and CD.

![arch](https://raw.githubusercontent.com/SaiHarshaK/concurrency-9/master/flowchart.png?token=AdPkfxCyU_IHJvdDY9bgF6jKwLmcRKHoks5cl5W_wA%3D%3D)

## Dependencies
There are no third party go packages being used out of the ones in this repository.
We use Google APIs for distance/traffic/map data, credentials need to be provided in - 
* [```externalApi.go```](server/externalApi.go) - for using Google APIs (distance/traffic)
* [```form.html```](public/form.html) - for using Google APIs (map)

**Jenkins** and **Docker** are used for CI/CD and containerisation.
## Instructions
To run the application do the following :
- cd into your go workspace
``` cd $GOPATH/src ```
- clone the repository
``` git clone git@github.com:SaiHarshaK/concurrency-9.git ```
- run the main.go
``` go run main.go ```
## Contributor Instructions

Run the following command to get the tools that run during pre-commit checks

```bash
go get golang.org/x/tools/cmd/goimports && go get golang.org/x/lint/golint && git config core.hooksPath .githooks
```
Follow the following comment format

```
\\<function name>, <description>
\\<description>
\\
\\	Inputs: <name>[, description] i.e. type[, repeat].
\\	Outputs: <name>[, description] i.e. type[, repeat].
```

## About

This project is a partial fullfillment for CS2433 (Principles of Programming Languages II) offered by Dr. Saurabh Joshi at IIT Hyderabad in Spring'19 semester.

## Contributors

Sai Harsha Kottapalli  
Sagar Jain  
Tanmay Renugunta  
Bogga Srinivas  
