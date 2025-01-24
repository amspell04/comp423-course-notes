# **Setting up a Dev Container for Rust**

* Primary author: [Amelia Spell](https://github.com/amspell04)

* Reviewer: [Lindsay Bean](https://github.com/lcbean)


In this tutorial you will be introduced to the programming language, Rust. We will go over how to install Rust, set up a development container from scratch, and then create your very first Rust project!

To complete this tutorial you will need a few prerequisites:

1. **A GitHub account**: [Github](https://github.com)
2. **VSCode Text Editor**: [Install VSCode](https://code.visualstudio.com/download)
3. **Git command-line tool installed**: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
4. **Docker installed**: [Install Docker](https://www.docker.com/products/docker-desktop/)

## **Getting Started with Rust**

Before we create our development container and our first Rust project, we need to install Rust! 
To do this we will use the Rust installer and version management tool called RustUp. 

### Install for macOS, Linux, & other unix-like operating systems:

Open a terminal or command prompt on your local machine and run the following snippet of code:

``` py title="Run the RustUp installer"

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

### Install for windows and other systems:

Visit [this link](https://forge.rust-lang.org/infra/other-installation-methods.html) and download the correct installation package for your system 

### Tips and tricks for navigating this Rust tutorial

**Hot Tip** Create a folder in your file system to hold your Rust projects! Give this folder an important name that you will be able to remember later on to make finding your Rust projects easier. 

Installation with RustUp comes with a tool called **Cargo**. This command-line tool is used to build Rust projects and manage packages. We will become familiar with the capabilities of this tool in the next few steps!


## **Creating a Directory for our Project and Initializing Git!**

In these next few steps we will create our Rust project directory, initialize Git, and connect our local repository to a remote repository in GitHub!

### Creating our project directory and initialize Git 
1. Open your terminal or command prompt and run the following commands:
``` 
cargo new hello-comp423 --vcs none
cd hello-comp423
```
*What do these commands do?* The first command creates a new Rust project directory and disables automatic repository initialization. The second command enters the directory we just made.
2. Initialize a git repository by running: 
``` 
git init
```
    *What does this command do?* This initializes the current directory as an empty GitHub repository.
3. Create a README file for the project by running: 
``` 
echo "# My First Rust Project!" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Creating the remote repository in Github 

1. Login to your [Github](https://github.com) Account and navigate to Create a New Repository page.
2. Fill in the details for your repository as follows: 
    * **Repository Name:** hello-comp423
    * **Description:** "My very first Rust project!"
    * **Visibility:** Public
3. Click Create Repository 
4. Navigate back to the terminal running your project directory.
5. Add the GitHub repository as a remote by runnng the following command: 
``` 
git remote add origin https://github.com/<your-username>/comp423-course-notes.git
```
    **Remember** replace "your-username" with your GitHub profile username.
6. Do not initialize the repository with a README, .gitignore, or license.
7. Click **Create Repository**

### Linking your local repository to the remote

1. 
2. 
3. 
4. 
 


Congrats! You just set up and initialized your directory in GitHub!


## **Creating a Development Container for our Project**
1. Open the hello-comp423 directory in VSCode.
2. Inside this folder you will need to create a new file with the file name .devcontainer.json.
3. Open this file and insert the following snippet of code: 
``` py title="Insert into .devcontainer.json"
{
    "name": "Rust Development Environment",
    "image": "mcr.microsoft.com/devcontainers/rust:latest",
    "customizations": {
        "vscode": {
            "extensions": [
                "rust-lang.rust-analyzer"
            ]
        }
    }
}
```
    Explanation of the configuration here.......

4. Before we continue, we should check our version of Rust by running the following command in the VSCode terminal: 
```
rustc --version
```

5. Go to the extensions tab of VSCode, this tab looks like a square with one piece leaving.
6. Search for and install the Dev Containers VSCode extension.
7. Open the command pallette. macOS shortcut: command + shift + p. Windows shortcut: ctrl + shift + p.
8. In the command pallette enter >Dev Containers: Open Dev Container.
9. This will build your development container! You will know you are connected to you container when you see this in the bottom left corner of your screen:
    **Note** When closing your and reopening your project you will need to reopen your dev container. You can do this by opening the command pallette again and running >Dev Containers: Reopen in Container.

Congrats! You have now successfully set up your Rust development container!



## **Writing your First Rust Program!**

Time to write a Rust program! In good tradition we will be writing a "Hello World" inspired program. 

1. Navigate to the src/main.rs file in your project directory. 
2. Edit the "Hello World" statement to say "Hello COMP423".
3. Now open a terminal in your VSCode window and run the following command to compile your project:
```
cargo build
```
    *What does this command do?* This command compiles our project similar to running gcc in C! 
4. Lastly, run the following command to run your program:
```
cargo run
```
    *What does this command do?* This command executes our program.

If you switch your view from terminal to output you should see Hello COMP423. Congrats! You have successfully installed Rust, set up a development container from scratch, and created your very first Rust project!


### Additional Information for Mastering Cargo

Some more examples of ways you might use the Cargo tool can be found below. Remember to run these commands in the terminal of VSCode in your proejct directory!

``` py title="Test your Rust project"
cargo test
```

``` py title="Build documentation for your Rust project"
cargo doc
```


## Sources 

 [Dev Container Setup](https://www.luisquintanilla.me/posts/setting-up-rust-dev-env-devcontainers-vscode/)

 [Rust Official Site for Setup](https://www.rust-lang.org/learn/get-started)


