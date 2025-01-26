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
echo "# Welcome to Go!" > README.md
git add README.md
git commit -m "add message here"
```


