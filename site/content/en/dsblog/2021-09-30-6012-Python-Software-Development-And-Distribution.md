---
draft: false
id: 6012    
title: "Python Software Development and Distribution"
date: '2021-09-30T15:50:00+05:30'
url: /dsblog/Python-Software-Development-and-Distribution
categories:
  - dsblog
tags:
  - Python Software Development 
  - Software Distribution
header:
  teaser: "/assets/images/dspost/dsp6012-Python-Software-Development-and-Distribution.jpg"
excerpt_separator: "<!--more-->"   
author: Hari Thapliyaal   
 
excerpt: "Learn about Python software development and distribution, focusing on best practices, tools, and methods for successful project deployment."
author_profile: true   
share: true   
toc: true   
toc_sticky: true 
mathjax: "true"
---



![Software Distribution](/assets/images/dspost/dsp6012-Python-Software-Development-and-Distribution.jpg)   

# Software Distribution

## Introduction   
We don’t develop any good and valuable piece of software from scratch. We use pieces of code written by others. This piece of code can be a service running on another machine or software written but kept in a repository. This service may be created by some other company, individual, our company, our team, or ourselves. So any software has two components, one, which is created by us, and we are responsible for the maintenance of that. Another component is a piece of software that is created by someone else, and we are not responsible for the maintenance of that.

Whoever creates a piece of software, it is his to maintain that. Why maintenance is required? Because of continuous up-gradation in the operating system, networking, and hardware, the old piece of software can be a cause of security threats, performance issues, parameter mismatch, service depreciation, etc. Suppose your friend created a software MatMul and this program is consumed by you in your software CalcFunc. If there is some change in OS or hardware driver or programming language version upgrade and MatMul was using some of the function from OS, but your friend does not update his software, then your CalcFunc will also fail. This will affect your customer and your services. This is the reason we should keep updating our software. After your friend updated his software, then it is your responsibility to rebuild your software again and share it with your customer.

As a data scientist, most of my work is around python, therefore, I am going to help you understand the software development, deployment, and distribution in data science projects and with python language. With respect to software distribution, there is no difference between data science and non-data science project, python and other than python projects.

## Data Science and Exploration
The success of data science and machine learning project heavily depends upon data exploration and research. For this work, you depend upon many open source libraries. You search these libraries, install them, experiment with your data using those libraries, and if it doesn’t work then go for another library. Other times you explore many libraries just to know which library would serve my purpose or which would perform best for my project data. This is quite an exhaustive and long process. Due to this rigorous exploration it more important for any data scientist to understand how different package creators creates their packages and how we should consume them. Similarly, when we create our packages then we need to learn about how to bundle them, ship them to the user and how to maintain and upgrade these packages.

## The different names for software piece
A piece of software written by you can have different names. It depends upon how you sell it, distribute it, or how people consume it. The different possible names may be Library, Product, API, Component, Widget, Plugin, Addon, Service, App, Application etc.

## Why different names for the software?
Let’s say in the real world you are a chair manufacture. But all those chairs are not consumed by you. Most of the chairs which you manufacture you produce to sell and make money or some sometimes for donations. But when a chair user is using a chair, he may use that chair in different situations and different environments. The environment may be open or close. It may wetty, dusty, dry or clean. It may be a factory or office or conference room. It may have cramp space or adequate space or a large hall. It may be for a party hall or a permanent seat in a office. It is possible that everyday chair moving from one location to another location or fixed at one place. Keeping all these in mind, you design chairs for different purposes. But the purpose of the chair doesn’t change. You don’t design chairs for sleeping unless it is some foldable design or people use it because of their circumstances. Because of different purposes, you put different adjectives before the chair so that buyer or user can identify your intentions of creating that. If your intention and his intention are the same then only he will explore around comfort, price, service, etc. otherwise he will not even talk with you.

Similarly, in software, let’s say you create software for login authentication. But this can be sold by you and consumed by users or by developers in different ways.

Library: Let’s say downloads X software and integrates it with his Y software. After the integration, if X software is changed by the creator then Y software will not break. When X software was shipped as a library, it may be a source code file or binary file or both. If only source code is given, then it is the consumer’s responsibility to build the binary file from the source code, without compilation, that library is of no use. Sometimes you can do little or desired modification in the source code and then compile it. Other times just take care of your OS, compiler and compiler version, hardware drivers, and other existing running software and then compile it. This X software is referred to as a library.

Component and library are used interchangeably.

API : Let’s say you install X software on your on-premise hardware or cloud hardware. After that you expose software as service X to others. Others are expected to pass some parameters in the required format, and it will return results. This is called API (application programming interface). API may be used by end-users directly or by other software developers or by other programs. It is the software developers’ (who is consuming service of the X software) responsibility to pass the parameters of correct type, adequate number of parameters, parameters in proper order. Otherwise, your software will not get the desired result and fail. But it is the API service creator’s responsibility to maintain his API without changing the interface. At any point in time, if he wants to change the interface because of some reason, he has to create a different service.

App or Application or Product: A piece of software that is shipped to the user’s machine and can be used independently. It is meant for end-user. For example, your Chrome browser or Microsoft Word or even Microsoft Office (many products integrated into one). The name App is used more in the sense of mobile phone product. For example, when you use Microsoft Word on android phone then it is App but when you use on laptop or desktop it is called Application.

Widget or Plugin or Addon: A piece of software which you use to expand the feature of existing software. Let’s say you like Microsoft Word, but you are not happy with the language and Grammar service. It may be  because you are writing in Japanese or some vernacular language and there is no good support. Or you are writing English philosophical poetry, but there is no good recommendation or good vocabulary support. Because of this, you want to consume service of something Grammarly or LanguageTool inside the word. For this you get add-on and install within the Microsoft Word. The name widget or plugin or add-on changes depending upon context, but the purpose and usage remain the same.

Service: Like incomes tax or GST portal. When you create software, but you don’t want to ship it because of many reasons, then you put software on your hardware or your rented hardware and give it to users to consume. It is like API, but the concept of API parameters is not there. It is like a product, but it is not your responsibility to update the hardware or platform where it is hosted.

## Why update your software?
The creator of the software piece has to maintain it. If your software piece is continually maintained and latest at any point in time, then the people who are consuming that software during development don’t hesitate to use it. Otherwise, the user may think that the creator is out of business or dead or the product is not worth using, therefore the creator is not updating.

During your development process, you may have consumed dozens of other packages and your final product may be complex enough which is beyond your jupyter notebooks. Now, how do you make sure that this software created by you should work on the production system without fail? For that first, you need to freeze all the packages you have used. After that you need to ensure these packages are available on all those machines which are using your code or software, either in development or testing or production.

## Freezing Environment
During development when we have installed everything needed for our work, that time our environment is stable. It is a good idea to freeze the development environment. Doing so helps us in transferring our software with this environment to the next machine. In the future, when we want to use the old environment for updating an existing (old) software code, we can use this frozen environment. The command to freeze is given below. This will create txt file and put the name of all the libraries along with their version in a requirmentx.txt file. 

pip freeze > requirements.txt

In the future whenever you want to create the same environment using this txt file you need to write the following command, and you can create the same environment.

python -m pip install -r requirements.txt


## Virtual Environment
As discussed earlier, during software development, we use existing and stable pieces of software. This needs to be installed on our machine. But, we may be working on multiple software simultaneously or some previously developed software need to up updated from our machine. In this process, it is quite possible that different software which we are developing or updating, or supporting have different versions of the same software/library which our different software we are referring, or calling. How to maintain the library of multiple versions of the same software so that the software which we are creating doesn’t have any conflict with other software which we are developing or maintaining in parallel?

Virtual environments solve this problem. A virtual environment can be created using many software. There are many software packages for creating virtual environments, but I am going to discuss conda, virtualenv and virtualenvwrapper

### Virtual Environment Using python
You can create virtual environment at any place on hard disk. You need to decide a directory where you want to place in your virtual environment and run this command.

python3 -m venv tutorial-env

The problem with this approach is very soon you will go crazy with dozens of virtual environments in the different directories, and it will be extremely difficult to manage them. You don’t know how many virtual environments are there on your machine. The second limitation of this approach is sometimes a virtual environment can be used for multiple projects, but if you keep a virtual environment project in a specific folder, you need to remember which environment in which project or folder.

After creating the environment to activate the installed environment on Windows, you can use the following command.

tutorial-env\Scripts\activate.bat

To activate installed environment on Unix/Mac

source tutorial-env/bin/activate

To delete the environment, you just delete the folder, and it is over.

## What are the different ways to distribute a python software?
The Python ecosystem has several other packaging and distribution formats beyond "egg" and "wheel". Each format serves different purposes, whether for source distribution, binary distribution, or specific use cases like environments or archives. Here’s an overview of the main formats:

### 1. **Source Distribution (sdist)**
   - **File Extension**: `.tar.gz` (commonly) or `.zip`
   - **Description**: This is a source distribution that contains the package’s source code. It typically includes a `setup.py` file, along with any Python files, modules, and other resources needed to install the package.
   - **Use Case**: When you need to distribute the source code of a package so that it can be built and installed on any system with a compatible Python environment.
   - **Command to Create**: `python setup.py sdist`

### 2. **Built Distribution (bdist)**
   - **File Extension**: Various (e.g., `.tar.gz`, `.zip`, platform-specific)
   - **Description**: A built distribution contains files that are pre-compiled for a specific platform and Python version, making it faster to install.
   - **Use Case**: When you need to distribute a package in a pre-built form, making it easy to install without needing to compile the code.
   - **Command to Create**: `python setup.py bdist`

### 3. **Binary Distribution**
   - **File Extension**: `.whl` (Wheel) or `.egg`
   - **Description**: These are pre-compiled binary distributions that are platform and Python-version specific. Wheel is the preferred format today.
   - **Use Case**: When distributing compiled extensions or large packages to ensure quick installation and compatibility with the user’s environment.
   - **Command to Create**: `python setup.py bdist_wheel`

### 4. **Executable Installer**
   - **File Extension**: `.exe` (Windows), `.msi` (Windows Installer), `.dmg` (macOS)
   - **Description**: These formats are used for platform-specific executable installers that can install Python packages on the target system.
   - **Use Case**: Often used for distributing standalone Python applications or large frameworks that include all dependencies and Python itself.
   - **Command to Create**: `python setup.py bdist_wininst` (Windows), or other platform-specific tools.

### 5. **Python Archive (pyz)**
   - **File Extension**: `.pyz`
   - **Description**: This format is a zip archive that can be executed directly by the Python interpreter. It packages a Python application into a single file.
   - **Use Case**: Useful for distributing standalone Python applications that can be run without needing to be installed in a Python environment.
   - **Tool**: `shiv`, `zipapp`

### 6. **Environment Formats**
   - **Conda Environment**: `.yml` files are used to describe and create environments using the Conda package manager.
   - **Pipenv Lockfile**: `Pipfile.lock` is used by Pipenv to create deterministic Python environments.

### 7. **Requirements File**
   - **File Extension**: `.txt` (typically named `requirements.txt`)
   - **Description**: A simple text file listing Python packages with specific versions that should be installed.
   - **Use Case**: Widely used to specify dependencies for a Python project, which can be installed using `pip`.

### 8. **Python Wheel Cache**
   - **File Extension**: `.cache`
   - **Description**: Used by pip to store pre-compiled wheels that can be reused across installations.
   - **Use Case**: Speeds up the installation process by reusing already built wheels.

### Summary of Formats:

| **Format**            | **File Extension** | **Purpose**                                          | **Preferred Today** |
|-----------------------|--------------------|------------------------------------------------------|---------------------|
| **Source Distribution** | `.tar.gz`, `.zip`  | Distributing source code                             | Yes                 |
| **Built Distribution**  | Various            | Pre-built code for specific platforms                | Yes                 |
| **Wheel**               | `.whl`             | Modern binary distribution                           | Yes                 |
| **Egg**                 | `.egg`             | Older binary distribution                            | No                  |
| **Executable Installer**| `.exe`, `.msi`     | Platform-specific installers                         | Yes (platform use)  |
| **Python Archive (pyz)**| `.pyz`             | Executable Python applications                       | Yes                 |
| **Environment Formats** | `.yml`, `Pipfile.lock` | Describing Python environments                      | Yes                 |
| **Requirements File**   | `.txt`             | Listing dependencies for `pip`                       | Yes                 |
| **Wheel Cache**         | `.cache`           | Reusing built wheels to speed up installs            | Yes                 |

These formats help manage, distribute, and deploy Python code and applications in different environments, ensuring that dependencies are met and installations are as smooth as possible.

### Virtualenvwrapper
As mentioned above virtualenv has many limitations and to overcome a wrapper is created around virtualenv this wrapper is called virtualenvwrapper. You can install this on your base environment as below. If you are interested in all the commands of virutualenvwrapper you can search for that on another place in internet.

pip install virtualenvwrapper

Virtualenvwrapper helps in following

* Organizes all of your virtual environments in one location
* Provides methods to help you easily create, delete, and copy environments
* Provides a single command to switch between environments

### Virtual Environment Using Conda
Conda is a package manager. It helps in creating, installing and removing package. Anaconda and Miniconda are two stores that have all the tools which are managed by Conda. If you have 3GB of space on your machine and looking for serious data science project then you can go for Anaconda, if you have less disk space or just looking for temporary exploration then you can install Miniconda. 

To create a virtual environment on Windows machine you can use 

```
Conda create -n conda-env python=3.7
```

To activate any specific conda environment you can use

```
Conda activate env_name
```

To deactivate an existing conda environment you case use

```
Conda deactivate
```

To get list of all the packages install in a conda environment 

```
Conda list
```

To get a list of all the Conda environment 

```
Conda list env
```

You can create any many environments as you want, depending upon hard-disk space available on your machine. You can work in all the environments simultaneously. All the environments are saved in \Users\admin\anaconda3\envs

If you want to learn more about Conda, then you can explore some resources on the internet.