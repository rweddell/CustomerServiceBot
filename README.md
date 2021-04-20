# CustomerServiceBot-RW
Example customer service chatbots of various complexities and implementations

## Description
This project uses a python/jupyter to train and interact with chatbots. The use case is in the form of a customer service representative at a bank.

It is recommended to be run in a virtual environment to avoid collisions between different Python package versions.

In this repo are two different implementations of chatbots. One uses a model which returns canned responses based on the classification of the intent of user input. The second uses natural language generation to create a response to user input based on conversation history. 

## Thought process and development
The original intent of this project was to explore the viability of implementing a chatbot in a customer-service space, but to use natural language generation. The state-of-the-art is a PersonaChat, which uses a double-headed BERT model and a specifically formatted dataset. The dataset uses a personality as well as considerations of chat history to generate a response. 

```
You: hi can I open a new account?
Bot: youre trying to open a new account. is that right?
You: yes
Bot: i can log a request. please give me your first and last name.
You: my name is robert weddell
Bot: a representative of botbank. is there anything else i can help with?
You: can I open a new account?
Bot: a request has been logged for your account. is there anything else i can help with?
You: can you tell me my account balance?
Bot: thank you. a request has been logged for your account. what else i can help with?
You: account balance
Bot: you want to check your account balance. is that correct?
You: yes
Bot: thank you. i just need to ask a few questions. please give me your first and last name
You: my name is lester morrison
Bot: your account balance is $ 354456. is there anything else i can help with?
You: no that's all
Bot: thank you for using botbank.

You: hours of operation
Bot: all botbank locations are open 7am to 4pm monday through friday! what else i can help
You: can I open a new account?
Bot: you want to open an account. is that right?
You: yes
Bot: thank you. i just need to ask a few questions. please give me your first and last name
You: lester morrison
Bot: thank you.
You: did you open a new account?
Bot: you are trying to open a new account. is that right?
You: yes
Bot: i can log a request. please give me your first and last name.
You: lester morrison
Bot: glad i could help. thanks for choosing botbank have a nice day.
```


## Creating a virtual environment with venv
Virtual environments can be created using Conda or Virtualenv.

This is a brief overview of how to create virtual environments. More details can be found on the [source site](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/#:~:text=To%20create%20a%20virtual%20environment,virtualenv%20in%20the%20below%20commands.&text=The%20second%20argument%20is%20the,project%20and%20call%20it%20env%20.).

If you haven't already, download the latest version of virtualenv using pip.

```python
pip install virtualenv
```

Navigate to the directory where you want to work and create a virtual environment.

```python
virtualenv environment_name
```

Activate your environment by running the activation script.

```python
# windows and colab
environment_name\Scripts\activate

# mac and linux
source env/bin/activate
```

When the environment is not in use, it can be deactivated.

```python
deactivate
```
