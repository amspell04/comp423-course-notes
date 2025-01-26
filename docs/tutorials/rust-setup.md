# **Setting up a Dev Container for Rust**

* Primary author: [Amelia Spell](https://github.com/amspell04)

* Reviewer: [Lindsay Bean](https://github.com/lcbean)


In this tutorial you will be introduced to the programming language, Rust. Rust is a systems programming language that allows more control of memory management. Throughout this tutorial we will learn how to set up a development container from scratch and then create our very first Rust project!

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
A. Open your local terminal or command prompt and run the following commands:
``` 
mkdir hello-comp423
cd hello-comp423
```

!!! info "What do these commands do?"

    The first command creates a new Rust project directory and disables automatic repository initialization. The second command enters the directory we just made.

B. Initialize a git repository by running: 
``` 
git init
```
!!! info "What does this command do?"
    This initializes the current directory as an empty GitHub repository.

C. Create a README file for the project by running: 
``` 
echo "# My first Rust Project" > README.md
echo "Development container setup thanks to: (https://amspell04.github.io/comp423-course-notes/tutorials/rust-setup/)" >> README.md
git add README.md
git commit -m "Initial commit with README"
```

### Creating the remote repository in Github 

A. Login to your [Github](https://github.com) Account and 

B. Navigate to your repository page and click **New**.

C. Fill in the details for your repository as follows: 

* **Repository Name:** hello-comp423
* **Description:** "My very first Rust project!"
* **Visibility:** Public

D. Do not initialize the repository with a README, .gitignore, or license.

E. Click **Create Repository**


### Linking your local repository to the remote

A. Return to your local terminal/command prompt which has your project directory opened.
B. Run the following command to add the GitHub repository as a remote:
``` 
git remote add origin https://github.com/<your-username>/hello-comp423.git
```
    **Remember** replace "your-username" with your GitHub profile username.
C. Run the command below
``` 
git branch
```
If the branch is **not** named main, run the command below:
``` 
git branch -M main
```
D. Push your local commits to the GitHub remote repository using the following commands:
``` 
git push --set-upstream origin main
``` 
E. Visit your remote repository in Github and refresh the screen. You should now see that the commit made in step 4 of "Creating our project directory and initializing Git" is in your remote repository!
 

**Congrats!** You just created your Rust project directory, initialized Git, and connect the local repository to the remote repository in GitHub!


## **Creating a Development Container for our Project**
A. Open the hello-comp423 directory in VSCode.

B. Go to the extensions tab of VSCode, this tab looks like a square with one piece leaving.

C. Search for and **install the Dev Containers VSCode extension**.

D. Now create a .devcontainer directory in the root of your project.

E. Inside this .devcontainer directory you will need to create a new file with the file name:
``` 
devcontainer.json
``` 
F. Open this file and insert the following snippet of code: 
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
    * **extensions**: Installs any needed extensions automatically. In this case, thte official ```rust-analyzer``` VSCode plugin by the Rust Programming Language Group.

G. Now, open the command pallette. macOS shortcut: ``command + shift + p``. Windows shortcut: ``ctrl + shift + p``.

H. In the command pallette enter ``>Dev Containers: Reopen in Container``. 

I. This will build your development container! This may take some time to load. You will know you are connected to you container when you see a blue rectangle in the bottom corner of your screen that says "Dev Container: Rust Development Environment".

J. Before we continue, you should check your version of Rust by running the following command in the VSCode terminal: 
```
rustc --version
```
    You should see version 1.83.0 or greater if a later version has been released since the writing of this tutorial.

**Congrats!** You have now successfully set up your Rust development container!

!!! tip
    When closing and reopening your project you will need to reopen your dev container. You can do this by opening the command pallette again and running >Dev Containers: Reopen in Container. Remember to give the environemnt time to load.



## **Writing your First Rust Program!**

Time to write your first Rust program! In good tradition we will be writing a "Hello World" inspired program. 

A. Make sure that you are inside your hello-comp423 directory in VSCode and that the dev container is running.

B. Open a terminal inside VSCode and run the following command:
```
cargo new hellocomp --vcs none
```
!!! info "What does this command do?"
    This command will create a new Rust project named "hellocomp"! The --vcs none flag will make sure that the cargo new command does not create a new git repository.

C. Navigate to the src/main.rs file in your project directory. 

D. Edit the default "Hello, World!" statement to say "Hello COMP423" and save the file.

E. Now return to the terminal in your VSCode window and run the following commands to compile your project:
```
cd hellocomp
cargo build
```
!!! info "What do these commands do?"
    The first command enters the hellocomp Rust project we created in the previous cargo command. We must enter this project directory for the terminal to have access to the necessary files to execute the program. The second command, ```cargo build```, compiles our project similar to running gcc in C! When a program is compiled it is translated from the high-level language we know, Rust, to a machine-readable binary file that can be executed by the compiler. The cargo build command just compiles your program into an executable format, it does **NOT** execute the program! 

F. Lastly, run the following command to run your program:
```
cargo run 
```
OR
``` 
cargo run main.rs
```

!!! info "What does this command do?"
     This command causes the compiler to compile our project **AND** execute. This is different from ```cargo build``` as ``` cargo run``` actually executes the binary file while the cargo build command just compiles the binary file. Using ``` cargo build ``` alone is good to use for debuggging your program, and using cargo run is good for when you are ready to execute your program!

G. In the terminal after the cargo run command you should see "Hello COMP423" output! 

**Congrats!** You have successfully set up a development container from scratch and created your very first Rust project!


H. To commit and push your changes to your github repository, run the following lines of code: 

``` 
    git add . 
    git commit -m "Hello COMP423"
    git push origin main
```

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


