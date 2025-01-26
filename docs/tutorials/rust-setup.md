# **Setting up a Dev Container for Rust**

* Primary author: [Amelia Spell](https://github.com/amspell04)

* Reviewer: [Lindsay Bean](https://github.com/lcbean)


In this tutorial you will be introduced to the programming language, Rust. We will go over how to install Rust, set up a development container from scratch, and then create your very first Rust project!

## **Tutorial Prerequisites**

To complete this tutorial you will need a few prerequisites:

1. **A GitHub account**: [Github](https://github.com)
2. **VSCode Text Editor**: [Install VSCode](https://code.visualstudio.com/download)
3. **Git command-line tool installed**: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
4. **Docker installed**: [Install Docker](https://www.docker.com/products/docker-desktop/)

!!! tip "Hot Tip"

    Create a folder in your file system to hold your Rust projects! Give this folder an important name that you will be able to remember later on to make finding your Rust projects easier. 


## **Creating a Directory for our Project and Initializing Git!**

In these next few steps we will create our Rust project directory, initialize Git, and connect our local repository to a remote repository in GitHub!

### Creating our project directory and initializing Git 
1. Open your local terminal or command prompt and run the following commands:
``` 
mkdir hello-comp423
cd hello-comp423
```

!!! info "What do these commands do?"

    The first command creates a new Rust project directory and disables automatic repository initialization. The second command enters the directory we just made.

2. Initialize a git repository by running: 
``` 
git init
```
!!! info "What does this command do?"
    This initializes the current directory as an empty GitHub repository.

3. Create a README file for the project by running: 
``` 
echo "# My first Rust Project" > README.md
echo "Development container setup thanks to: (https://github.com/amspell04/comp423-course-notes)" >> README.md
git add README.md
git commit -m "Initial commit with README"
```

### Creating the remote repository in Github 

1. Login to your [Github](https://github.com) Account and 
2. Navigate to your repository page and click **New**.
3. Fill in the details for your repository as follows: 
    * **Repository Name:** hello-comp423
    * **Description:** "My very first Rust project!"
    * **Visibility:** Public
4. Do not initialize the repository with a README, .gitignore, or license.
5. Click **Create Repository**


### Linking your local repository to the remote

1. Return to your local terminal/command prompt which has your project directory opened.
2. Run the following command to add the GitHub repository as a remote:
``` 
git remote add origin https://github.com/<your-username>/hello-comp423.git
```
    **Remember** replace "your-username" with your GitHub profile username.
3. Run the command below
``` 
git branch
```
If the branch is **not** named main, run the command below:
``` 
git branch -M main
```
4. Push your local commits to the GitHub remote repository using the following commands:
``` 
git push --set-upstream origin main
``` 
5. Visit your remote repository in Github and refresh the screen. You should now see that the commit made in step 4 of "Creating our project directory and initializing Git" is in your remote repository!
 

Congrats! You just created your Rust project directory, initialized Git, and connect the local repository to the remote repository in GitHub!


## **Creating a Development Container for our Project**
1. Open the hello-comp423 directory in VSCode.
2. Go to the extensions tab of VSCode, this tab looks like a square with one piece leaving.
3. Search for and install the Dev Containers VSCode extension.
4. Now create a .devcontainer directory in the root of your project.
5. Inside this .devcontainer directory you will need to create a new file with the file name:
``` 
devcontainer.json
``` 
6. Open this file and insert the following snippet of code: 
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
!!! info "Let's discuss this configuration"
    
    * **name:** Gives a descriptive name to your current development container.
    * **image:** This configures our development container to pull the latest Rust base image from Microsoft for Docker to use to create our environment. Essentially, this allows us to run the Rust language while in the container without having to install any software onto our local machine! The Rust software instead will exist inside our container thanks to pulling the base Rust image. 
    * **customizations:** Adds useful configurations to VSCode, in this scenario it will download the rust-analyzer extension. Adding the extensions into the automatic configuration file for our development container ensures that other engineers working on your project will not be missing any necessary extensions. 

7. Now, open the command pallette. macOS shortcut: command + shift + p. Windows shortcut: ctrl + shift + p.
8. In the command pallette enter >Dev Containers: Reopen in Container.
9. This will build your development container! You will know you are connected to you container when you see a blue rectangle in the bottom corner of your screen that says "Dev Container: Rust Development Environment".
10. Before we continue, you should check your version of Rust by running the following command in the VSCode terminal: 
```
rustc --version
```
    You should see version 1.83.0

Congrats! You have now successfully set up your Rust development container!

!!! note
    When closing and reopening your project you will need to reopen your dev container. You can do this by opening the command pallette again and running >Dev Containers: Reopen in Container.



## **Writing your First Rust Program!**

Time to write a Rust program! In good tradition we will be writing a "Hello World" inspired program. 

1. Make sure that you are inside your hello-comp423 directory in VSCode and that the dev container is running.
2. Open a terminal inside VSCode and run the following command:
```
cargo new hellocomp --vcs none
```
!!! info "What does this command do?"
    This command will create a new Rust project named "hellocomp"! The --vcs none flag will make sure that the cargo new command does not create a new git repository.

1. Navigate to the src/main.rs file in your project directory. 
2. Edit the default "Hello, World!" statement to say "Hello COMP423" and save the file.
3. Now return to the terminal in your VSCode window and run the following commands to compile your project:
```
cd hellocomp
cargo build
```
!!! info "What do these commands do?"
    The first command enters the hellocomp Rust project we created in the previous cargo command. We must enter this project directory for the terminal to have access to the necessary files to execute the program. The second command compiles our project similar to running gcc in C! When a program is compiled it is translated from the high-level language we know, Rust, to a machine-readable binary file that can be executed by the compiler.
4. Lastly, run the following command to run your program:
```
cargo run
```
    *What does this command do?* This command causes the compiler to execute the binary file created when running the cargo build command. This is different from cargo build as cargo run actually executes the binary file while the cargo build command just compiles the binary file.
5. In the terminal after the cargo run command you should see "Hello COMP423" output! 

Congrats! You have successfully set up a development container from scratch and created your very first Rust project!


### Additional Information for Mastering Cargo

Some more examples of ways you might use the Cargo tool can be found below. Remember to run these commands in the terminal of VSCode in your proejct directory!

``` py title="Execute a unit test within your Rust project"
cargo test
```

``` py title="Build documentation for your Rust project"
cargo doc

```
``` py title="See documentation for cargo commands"
cargo help
```

Visit [this site](https://doc.rust-lang.org/cargo/commands/index.html) for more information on helpful cargo commands to use with Rust!

## Sources 

 [Dev Container Setup](https://www.luisquintanilla.me/posts/setting-up-rust-dev-env-devcontainers-vscode/)

 [Rust Official Site for Setup](https://www.rust-lang.org/learn/get-started)

 [Cargo Commands Documentation](https://doc.rust-lang.org/cargo/commands/index.html)


