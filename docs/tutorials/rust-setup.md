# Setting up a dev container for Rust

* Primary author: [Paul Yang](https://github.com/Paulyang80)
* Reviewer: [Daniel Wang](https://github.com/danielwang23)

# Let's get started

Let's begin our Rust Journey, below are what we are going to discuss in this tutorial:
- Introduction
- Prerequisites
- Setting Up Git Repository
- Configuring the DevContainer
- Verifying Rust Version
- Creating your first project
- Write your first program, "Hello COMP423"
- Compiling and Running the Program
- Testing and Sharing

## Introduction
Rust is a general-purpose programming language emphasizing performance, type safety, and concurrency. It enforces memory safety, meaning that all references point to valid memory. It does so without a traditional garbage collector; instead, memory safety errors and data races are prevented by the "borrow checker", which tracks the object lifetime of references at compile time. -- wikipedia

### What will we do in this tutorial
- Setting up a DevContainer for Rust.
- Writing a simple "Hello COMP423" program.
- Compiling and running the program.

## Prerequisites
- Installed VSCode with the Remote - Containers plugin.
- Git installed locally and a GitHub account.
- Basic understanding of Git workflows and containerized development.

## Setting Up the Git Repository
- Explain how to:
    - Create a new Git repository:
	```Bash
	     git init 
	```
    - Create a new directory structure:
    ```Bash
         mkdir -p docs/tutorials 
         cd docs/tutorials
	```
    - Add a `.gitignore` file for Rust:
	```Bash
		 echo "target/" >> .gitignore
	```
- What is `.gitignore`?
	- The `.gitignore` file tells Git which files or directories to ignore in version control. For Rust projects, ignoring the `target/` directory is essential because it contains compiled binaries and temporary files that are not necessary to track in your Git repository.
- You can see more tutorials [here](https://git-scm.com/docs/gittutorial) .
## Configuring the DevContainer
- Explain how to configure the [development container for Rust](https://hub.docker.com/r/microsoft/devcontainers-rust):
	1. Create a `.devcontainer` folder:
	```Bash
		mkdir .devcontainer
		cd .devcontainer
		touch devcontainer.json
	```
	2. Write `devcontainer.json`:
```Json
	{
	  "name": "Rust DevContainer",
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
- Install [Rust Analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer) on VScode：
	- This extension provides support for the [Rust programming language](https://www.rust-lang.org/). It is recommended over and replaces `rust-lang.rust`.
### [What is a container](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-is-a-container)
- A standard package of software—known as a container—bundles an application’s code together with the related configuration files and libraries, and with the dependencies required for the app to run. This allows developers and IT pros to deploy applications seamlessly across environments.
## How to Start a DevContainer
When you open your project directory in **VS Code**, a prompt should appear asking if you want to reopen the folder in a DevContainer:
- Click **"Reopen in Container"**.
If the prompt does not appear, you can manually start the DevContainer:
1. Open the command palette using **Ctrl+Shift+P** (Windows/Linux) or **Cmd+Shift+P** (Mac).
2. Search for and select **"Reopen in Container"**.
3. VS Code will automatically pull the required Docker image and start the container.

## Verifying Rust Version
- Run the following commands to check if Rust is installed properly:
```bash
    rustc --version 
    cargo --version
```
- You should see:
```Bash
	rustc 1.83.0 (90b35a623 2024-11-26)
	cargo 1.83.0 (5ffbef321 2024-10-29)
```
## Creating your first project
- `Cargo new`
```Bash
	cargo new hello_comp423 --vcs none
	cd hello_comp423
```
- `cargo new` creates a simple Hello World project with a `main.rs` source code file and `Cargo.toml` [Cargo manifest](https://doc.rust-lang.org/cargo/reference/manifest.html) file.
```Bash
	src\
	    main.rs
	Cargo.toml
```
- `--vcs none`: preventsCargo from automatically creating a Git repository.

## Write your first program, "Hello COMP423"
- Open the file /hello_comp423/src/main.rs
```Rust
	fn main() {
	    println!("Hello COMP423!");
	}
```
## Compiling and Running the Program
- `cargo run`: Run a binary or example of the local package.
	- ```
	```Bash
	$cargo run
	Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.01s
    Running `target/debug/hello_comp423`
	Hello COMP423!
	```
- `cargo build`: Compile local packages and all of their dependencies.
	- 
	```Bash
	$cargo build
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.06s
	```

## Testing and Sharing
- Push the repository to GitHub:
    - Add a `README.md`:
    ```Markdown
        # Hello COMP423 Rust Project Follow the tutorial here:
	```
    - Commit and push changes:
```Bash
        git add . 
        git commit -m "Initial commit" 
        git push origin main
```
## Reference
- [Rust (programming language)](https://en.wikipedia.org/wiki/Rust_(programming_language))
- [Rust 程式設計語言](https://rust-lang.tw/book-tw/title-page.html)
- [The Rust Programming Language](https://doc.rust-lang.org/book/title-page.html)
- [Rust Development Container Images](https://hub.docker.com/r/microsoft/devcontainers-rust)
- [Rust in Visual Studio Code](https://code.visualstudio.com/docs/languages/rust)
- [What is a container](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-is-a-container)
- [What files in a Cargo project should be in my .gitignore?](https://stackoverflow.com/questions/43667176/what-files-in-a-cargo-project-should-be-in-my-gitignore)
