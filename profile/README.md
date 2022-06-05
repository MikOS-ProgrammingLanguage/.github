# **🤖 The Mik Programming Language 🤖**

Mik is a general purpose c-like language that comes with a package manager!

## **Getting started**

### **1. Installing mic & mip**

    # 1
    git clone https://github.com/MikOS-ProgrammingLanguage/MicNewDawn.git
    # 2
    cd MicNewDawn
    # 3
    make
    # 4
    export PATH = "<your path to mik>:$PATH"
    # 5
    sudo mic -install

### **2. Basics of mic & mip**

Before we get started with the language itself, I should explain the compiler flags and package manager flags as well as how to upload your own packages to mip!

1. **MIK compiler flags**

| Command | Usage | Explanation|
|:--------|:-----|:-----------|
|    -i   |mic -i <path_to_file> |  Is used to specify the input file|
|-o|-o <path_to_destination>|Is used to specify the output file and it's location|
|-exec|mic -exec|Sets the compilation target to a binary. Is on by default|
|-ll|-ll|Sets the compilation target to llvm-ir|
|-sec-ign|mic -sec-ign "\<section1>,\<section2>,.."|Is used to ignore certain sections. This means that those sections will not be compiled. For example if you have a debug section you can use sec-ign to exclude this section from compilation|
|-install|sudo mic -install|Runs a setup for mic and mip. This step is necessary|

- **MIP compiler flags**

   | Command | Usage | Explanation |
   |:--------|:------|:------------|
   |install|mip install \<url>|Installs a mik package to the global system packages from github|
   |update|mip update|Updates all installed packages|
   |remove|mip remove \<package1> \<package2>, ...|Removes all specified packages from the global system directory|
   |init|mip init \<path_to_project>|Sets up a new mik project. Use a non existing directory to create a new directory. Use a '.' to init in the current directory|
   |milk|mip milk|"Milks" the milk.pkg file in the current project. This is used to basically set up a downloaded project. But I go into more detail on milk.pkg later|
   |list|mip list|Lists all installed package in a tree structure|
   |add|mik add \<url>|Installs a package to the .pkgs folder in your project|
   |help|mip help|Get info about all commands|

## **MIP (Mik package manager)**

### **1. A mik project**

A mik project consists of the following files

    ├ .gitignore
    ├ milk.pkg
    ├ .mik_pkgs/
    ├ src/
    ├ main.mik
    ⌊ Makefile

#### **milk.pkg**

milk.pkg is a file that is used to define rules on how to setup a project

- Commands

|Commands|Usage|Explanation|
|:--------|:-------|:------|
|package-name|package-name: \<your_package_name>|Is used to name your package|
|ignore|ignore: \<file_name>|Is used to remove a file when milked via "mip milk"|
|depends|depends: \<github_package_url>|Is used to install dependencies when milked|
|entry|entry: \<your_main_file_location>|Is used to set the main file of your project. Otherwise installed projects can't be used|
