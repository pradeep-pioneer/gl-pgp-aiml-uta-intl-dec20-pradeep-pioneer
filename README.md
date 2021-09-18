# PGP in AI & ML

This is the github classroom repository for the Post Graduate Program in AI & Machine Learning from Great Learning. This file outlines the structure and details about the owner of this repository.

```
Student Name: Pradeep Singh
Student Emails:
    pradeep.ansh.sumit@gmail.com
    contact@pradeep.vip
```

## Repository Structure

The repository is organized in folders such that each top level folder indicates a course module in the root of the repository. The modules are numbered in order and inside each module folder we will have folders for practice and assignments. The below markdown shows the example of structure of the repository

```
root-----
        |
        --- 01-program-overview -----------
                                          |
                                          --- assignments
                                          |
                                          --- practice
        --- 02-pre-work -------------------
                                          |
                                          --- assignments
                                          |
                                          --- practice
        --- 03-statistical-learning -------
                                          |
                                          --- assignments
                                          |
                                          --- practice
```

## Environment Setup

I will be using python 3.7 in a python virtual environment setup using miniconda. The below list lists down the pre-requisites for the environment.

1. [Miniconda](https://docs.conda.io/en/latest/miniconda.html)
2. [Docker Desktop](https://www.docker.com/products/docker-desktop): to be able to run GPU tools in a docker environment - I have a an NVIDIA RTX 2070 on my machine so I will try to utilize the GPU wherever possible.
3. Visual Studio Code: I will be using VS Code as an IDE for editing code (except for code in notebooks)

The next steps defined in this file are based on the [video guide](https://youtu.be/qrkEYf-YDyI) by [Prof. Jeff Heaton](https://www.youtube.com/channel/UCR1-GEpyOPzT2AO4D_eifdw) from [Washington University in St. Louis](https://engineering.wustl.edu/Programs/Pages/default.aspx).

### Step 1

After installing the above pre-requistes it's the time for us to setup our conda environment. I have 2 environments - for CPU and for GPU. The environment dependency files are with the following names:

- ```gl-tensorflow.yml```: This file defines the CPU environment dependencies.
- ```gl-tensorflow-gpu.yml```: This file defines the CPU environment dependencies.

To create the environment I will execute the following commands from a terminal/command prompt (on windows - you can run the cmd process).

```bash
# install jupyter notebooks
conda install -y jupyter
# navigate to the root of the repository
cd [REPO_ROOT]
conda env create -v -f <gl-tensorflow.yml | gl-tensorflow-gpu.yml>
conda activate <gl-tensorflow | gl-tensorflow-gpu>
# for CPU tensorflow env
python -m ipykernel install --user --name gl-tensorflow --display-name "GL-Python-3.7 (tensorflow)"
# for GPU tensorflow env
python -m ipykernel install --user --name gl-tensorflow-gpu --display-name "GL-Python-3.7 (tensorflow-gpu)"
conda deactivate
```

### Step 2.5 => For Tensorflow GPU support (optional only if you are using the gl-tensorflow-gpu).

Let's see if we have cudnn and cudatoolkit installed

```bash
conda activate gl-tensorflow-gpu
conda list
```
This command lists the packages installed in the current conda environment. **If you don’ t see ‘cudnn’ or ‘cudatoolkit’ package installed, then you need to install them.**

#### Find cudnn:

```bash
conda search cudnn
```

The output will be something like the one shown below (depending on the latest versions available)
| Name                       |Version           |Build       |Channel  |
|----------------------------|------------------|------------|---------|
|cudnn                       |7.1.4             |cuda8.0_0   |pkgs/main|
|cudnn                       |7.1.4             |cuda9.0_0   |pkgs/main|
|cudnn                       |7.3.1             |cuda10.0_0  |pkgs/main|
|cudnn                       |7.6.0             |cuda10.0_0  |pkgs/main|
|cudnn                       |7.6.0             |cuda10.1_0  |pkgs/main|
|cudnn                       |7.6.0             | cuda9.0_0  |pkgs/main|
|cudnn                       |7.6.4             |cuda10.0_0  |pkgs/main|
|cudnn                       |7.6.4             |cuda10.1_0  |pkgs/main|
|cudnn                       |7.6.4             | cuda9.0_0  |pkgs/main|
|cudnn                       |7.6.5             |cuda10.0_0  |pkgs/main|
|cudnn                       |7.6.5             |cuda10.1_0  |pkgs/main|
|cudnn                       |7.6.5             |cuda10.2_0  |pkgs/main|
|cudnn                       |7.6.5             | cuda9.0_0  |pkgs/main|
|cudnn                       |7.6.5             | cuda9.2_0  |pkgs/main|
|cudnn                       |8.2.1             |cuda11.3_0  |pkgs/main|

Run the following command or similar based on the output that you see.
```bash
conda install cudnn=8.2.1=cuda11.3_0
conda install tensorflow-gpu
conda list
```
Now you should be able to see the cudnn, cudatoolkit installed in your environment. Deactivate the environment.
```bash
conda deactivate
```

Now it's time to check our environments. We can execute the following commnads from the root of our repository

### Step 2
```bash
conda activate <gl-tensorflow | gl-tensorflow-gpu>
jupyter notebook
```

This will start the jupyter notebooks and open the default web browser with the user interface for jupyter notebooks.

To check the environment you can open the notebook in the [01-environment-check.ipynb](./00-check-environment.ipynb)

If there are no errors when executing the first code cell (second cell in the notebook) - the environment has been setup successfully.