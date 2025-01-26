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
echo "https://<your-username>.github.io/comp423-course-notes/tutorials/go-setup/" > README.md
git add README.md
git commit -m "Add initial README for Go project"
```
A remote repository is a version of your project stored on a network so that multiple people can review and make changes to it from different locations and computers. Let's turn your local repository into a remote one:

1. Navigate to the Create a New Repository page on GitHub
2. Fill in the details as follows:
    * __Repository Name__: hello-go
    * __Description__: "Following a Go tutorial."
    * __Visibility__: Public
4. Create Repository
5. Make your GitHub repository remote:
``` py
git remote add origin https://github.com/<your-username>/hello-go.git
``` 
6. Rename your default branch name to main if it is something different such as "master"
``` py
git branch -M main
``` 
7. Finally, push your local commits into the new repository
``` py
git push --set-upstream origin main
``` 

!!! note

    Origin is used as the name of your remote repository on the line above. You can choose a different name, but origin is the conventional choice.


## Setting Up DevContainer

1. Open VSCode and install the Go VSCode Plugin
2. Open your directory in VSCode, it should be called "hello-go"
3. Create a `.devcontainer` directory in the root of your project, and create a file inside with this path name: `.devcontainer/devcontainer.json`
4. Add the following code into the .json file:
``` json
{
    "name": "First Go Project",
    "image": "mcr.microsoft.com/devcontainers/go:latest",
    "customizations": {
        "vscode": {
            "settings": {},
            "extensions": ["golang.go"]
        }
    } 
}
```
!!! info

    `name` refers to a clear description of the container. `image` refers to the docker image used which in our case is the latest version of a Go environment. `extensions`
     includes any necessary extensions for our environment
### Additional Steps

5. Reopen your project in a VSCode Dev Container by pressing `Ctrl+Shift+P` or `Cmd+Shift+P` for Macs.
6. Type "Dev Containers: Reopen in Container," and select the option.
7. Your final step is to check the version of Go your dev container is running to make sure it is up to date. Open a new terminal in VSCode and run `go version`


## Your First Go Project

To create your first "hello world"-like Go project, follow the steps below!

*   Open your terminal and cd to your created directory:

`cd hello-go` 

*  Enable dependency tracking for your code

`$ go mod init example/hello`

`go: creating new go.mod: module example/hello`

*  In your text editor, create a file called "hello.go" to write the code below in:
``` py
package main
import "fmt"
func main() {
    fmt.Println("Hello COMP423")
}
```
## Running your Code
Type the following code into your terminal to see the greeting!

` go run . `

## Running using 'build'
Type the following code into your terminal to use Go's 'build' subcommand:

`go build hello.go`

This should create a file in your current directory where you can execute the binary directly with the following commands:
`./hello` for Mac

`hello.exe` for Windows 

!!! info
    This command is similar to the gcc command used to compile C programs into executables, or, files a computer runs on its operating system. The `build` subcommand compiles our source code into a binary executable file without executing it.


## Pushing Changes to GitHub Repository
1. Add and commit your changes with the following commmands:
``` bash
git add .
git commit -m "Hello COMP423"
```
2. Push the changes to GitHub:
``` bash
git push origin main
```


Congratulations! You have now created your first Go project inside of a dev container!

## Citations
I used the following resources to help me write this tutorial: 

1. COMP423 Git Fundamentals: https://comp423-25s.github.io/resources/git/ch2-git-fundamental-subcommands/#step-1-create-a-directory

2. COMP423 Remote Repositories https://comp423-25s.github.io/resources/git/ch4-git-remote-fetch-push-pull/

3. Go Documentation Tutorial: https://go.dev/doc/tutorial/getting-started

