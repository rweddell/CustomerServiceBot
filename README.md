# CustomerServiceBot-RW
Example customer service chatbots of various complexities and implementations

## Description

This project uses a jupyter notebook to train and run a chat bot. The training data is designed to reflect the use case of a customer service representative. 

It can be initiated in any environment, but it is recommended to be run in a virtual environment to avoid collisions between different Python package versions.

Virtual environments can be created using Conda or Virtualenv.

## Creating a virtual environment with venv

This is a brief overview of how to create virtual environments. More details can be found on the [source site](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/#:~:text=To%20create%20a%20virtual%20environment,virtualenv%20in%20the%20below%20commands.&text=The%20second%20argument%20is%20the,project%20and%20call%20it%20env%20.).

If you haven't already, download the latest version of virtualenv using pip.

```python
pip install virtualenv
```

Navigate to the directory where this file and create a virtual environment and create a virtual environment.

```python
venv environment_name
```

Activate your environment by running the activation script.

```python
# windows and colab
environment_name\Scripts\activate

# mac and linux
source env/bin/activate
```

When the environment is not use, it can be deactivated.

```python
deactivate
```

# Usage
Install the requirements.txt file in your venv.

```python
pip install requirements.txt
```

Start up jupyter lab

```python
jupyter lab
```

Open the notebook and follow the instructions embedded in the cells. 
