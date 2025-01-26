# Setting up a dev container for Go
* Primary author: [Margot Bohlin](https://github.com/margotbohlin)
* Reviewer: [Samhitha Pudipeddi](https://github.com/samhipudi)

## Introduction

This tutorial will walk you through creating a basic "Hello World"-like project in Go. You will set up a Dev Container and use Git to merge/push changes in your code and store your project's collective history.

## Prerequistes
Before beginning the tutorial, you should have these prerequistes:
1. GitHub- to track versions of your code
2. Git - to navigate throughout histories of your code and push changes 
3. Visual Studio Code - Any text editor will do, but VSCode is MY personal preference
4. Docker - this is where you will set up your Dev Container

## Getting Started with Git
You will want to create a new directory for every project you make. Let's call our directory "hello-go" because it is your first time using go
Copy the code below line by line into your terminal to create the directory, move into it, and turn it into a git repository:
``` py
mkdir hello-go
cd hello-go
git init
```
The next step involves creating a file within your workspace to include any additional explanation for your project. We call this file our README
``` py
echo "https://margotbohlin.github.io/comp423-course-notes/tutorials/hello-go/" > README.md
git add README.md
git commit -m "Add initial README for Go project"
```
A remote repository is a version of your project stored on a network so that multiple people can review and make changes to it from different locations and computers. Let's turn your local repository into a remote one:
``` py
git remote add origin https://github.com/<your-username>/hello-go.git
```
!!! note

    Origin is used as the name of your remote repository on the line above. You can choose a different name, but origin is the conventional choice.

# Creating a Remote Repository on GitHub
1. Navigate to the Create a New Repository page after logging into GitHub
2. Fill in the details as follows:
    * __Repository Name__: first-rust-project
    * __Description__: "Following a Rust tutorial."
    * __Visibility__: Public
4. Click Create Repository

# Link your Local Repository to GitHub
1. Add the GitHub repository as a remote
``` bash
git remote add origin https://github.com/<username>/first-rust-project.git
```
2. Rename your default branch name to main if it is not main already using the command below
``` bash
git branch -M main
```
3. Push your local commits to the GitHub repository
``` bash
git push --set-upstream origin main
```

## Setting Up the Development Enviornment

1. Open the `first-rust-project` directory in VS Code
2. Install the Dev Containers extension for VS Code
3. Create a `.devcontainer` directory in the root of your project with the following file inside:
`.devcontainer/devcontainer.json`
4. Add the following code into that file:
``` json
{
  "name": "First Rust Project",
  "image": "mcr.microsoft.com/devcontainers/rust:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["rust-lang.rust-analyzer"]
    }
  }
}
```


## Setting Up DevContainer

Open VSCode and install VSCode Remote-Containers extension. Now you can create your devcontainer directory and docker configuration using the code below:
``` py
mkdir .devcontainer
echo "FROM golang:1.20\nWORKDIR /workspace\nRUN apt-get update && apt-get install -y git curl && apt-get clean\nENV PATH=\"/go/bin:$PATH\"" > .devcontainer/Dockerfile
echo "{\n  \"name\": \"Go Dev Container\",\n  \"build\": { \"dockerfile\": \"Dockerfile\" },\n  \"settings\": { \"go.gopath\": \"/workspace\" },\n  \"extensions\": [\"golang.go\", \"ms-azuretools.vscode-docker\"],\n  \"forwardPorts\": [8080],\n  \"workspaceFolder\": \"/workspace\"\n}" > .devcontainer/devcontainer.json
git add .
git commit -m "Add dev container setup for Go development"
git push -u origin main
```
!!! info

    What is this doing? The above lines first create a directory to store configuration files for your dev container setup. You then create a new file within the directory, and a devcontainer configuration file (devcontainer.json). ".json" is a file format that uses human-readable language to store and communicate data objects. You are then adding these changes to staging, commiting them, and pushing them to main. 


## Your First Go Project


