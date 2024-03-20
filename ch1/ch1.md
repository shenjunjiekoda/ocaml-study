# Chapter1. Getting started.

## Opam and OCaml

For macos:
```shell
# Homebrew
brew install opam

# Macports
port install opam
```

**For Linux:** the preferred way to install **OCaml package manager** on Linux is to use the package manager of your distribution. For example, on Ubuntu:
```shell
apt-get install opam
```

Then, we install an **OCaml compiler** using the following command:
```shell
opam init # initialize opam
eval $(opam env)  # set up the environment

# install the given version of OCaml
opam switch create 4.13.1
eval $(opam env)  # set up the new environment

which ocaml  # check the path to the compiler
ocaml -version  # check the version of the compiler
```

This will install the latest version of OCaml (4.13.1) and set up the environment for it.

To check the installed version of OCaml, run:
```shell
ocaml --version
```

For windows, pleasse download and install the official installer from the official website: https://fdopen.github.io/opam-repository-mingw/.

## The Ocaml Toplevel

Ocaml comes with a built-in interactive environment called the Ocaml Toplevel. To start it, simply run:
```shell
ocaml
```

This will start the Ocaml Toplevel with a prompt `#` and we should type `;;` after we finished typing. You can type in expressions and see the results. For example:
```ocaml
# let x = 1 + 2;;
val x : int = 3

# let y = 2.0 +. 3.0;;
val y : float = 5.0

# let z = x + y;;
val z : float = 8.0
```

The Ocaml Toplevel is a powerful tool for experimenting with OCaml code. Press `Ctrl-D` to exit the Toplevel.

`utop` is another alternative, which is a more user-friendly version of the Ocaml Toplevel. It can be installed using `opam`:
```shell
opam install utop
```

To start `utop`, simply run:
```shell
utop
```

It supports line editing, history, real-time and context sensitive completion, colors, and more.

Or, you can try OCaml REPL online at https://try.ocamlpro.com/.

## Dune Build System

Dune is a build system for OCaml. It is similar to Make, but it is more powerful and easier to use. To install Dune, run:
```shell
opam install dune
```

To create a new project, run:
```shell
dune init
```

This will create a `dune` file in the current directory. The `dune` file is the main configuration file for Dune. It specifies the dependencies of the project, the build targets, and other options.

Here are some common Dune commands:
`dune build`: build the project. If no target is specified, it builds all targets.
`dune clean`: clean the build artifacts, remove the `_build` directory.
`dune runtest`: run the tests defined in the project.
`dune exec -- <executable>`: build and execute the specified executable. For example, `dune exec -- my_executable`.
`dune utop`: start an interactive environment (utop) with all the libraries and modules of the project loaded, for quick testing and exploration.
`dune build @install`: build all the files and libraries marked as install in the project.
`dune upgrade`: upgrade the dune configuration file of the project to the latest dune language version.
`dune init <component> <name>`: initialize a new project component, such as a library (lib) or an executable (exe). For example, `dune init exe my_executable` creates a new executable project.

### Your First Dune Project

Let's begin the helloworld example. Create a new directory called `hello_world` and navigate to it:

1. Initialize the project:
```shell
dune init project hello_world
```

Initializing a new Ocaml project with dune will create a new directory for the project and generate the `dune-project` file in the project root directory, which contains metadata and configuration for the project.

>`bin` directory: This directory contains executable files that can be built and executed.
>`lib` directory: This directory contains OCaml libraries that can be used by other parts of the project.
>`test` directory: This directory contains OCaml test suites that can be run using the `dune runtest` command.
>`_build` directory: This directory contains the build artifacts of the project.
>`<project_name>.opam` file: This file contains metadata about the project and its dependencies.

2. Build the project:
```shell
dune build
```

3. Run the program:
```shell
./_build/install/default/bin/hello_world
```

This will print "Hello, world!" to the console. We can also run the program directly using `dune exec`:
```shell
dune exec hello_world
```
