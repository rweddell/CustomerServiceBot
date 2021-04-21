# Customer Service bot using canned responses and bag-of-words

The content in /cs-cannedresponse is used to define a dataset and build a simple chatbot.  
The chatbot intakes user input and compares it against a database of 'intents'. 
Once the input has been classified a 'canned response' fitting the intent is returned to the user.  

## How to use this code
From command line clone the repository and install the requirements    
```
git clone https://github.com/rweddell/CustomerServiceBot-RW  
pip install -r ./CustomerServiceBot-RW/cs-cannedresponse/requirements.txt
```
Open [cs_cannedbot.ipynb](https://github.com/rweddell/CustomerServiceBot-RW/blob/main/cs-cannedresponse/cs_cannedbot.ipynb) and follow the instructions. Execute the cells when you are ready.  

## About the files
### cs_cannedbot.ipynb
A notebook which contains logic for processing a dataset as well as creating, training, and interacting with a chatbot.  
### cs_prompts.json
JSON file containing the dataset for training a chatbot as well as holding the responses given back to the user.   
The file is a list of intents with associated inputs and outputs.  
The chatting function references this file to pull the associated response once the user's input has been classified.  
### cs_training_data.json
This is the JSON representation of the conversations.txt file after it has been passed through make_dataset.ipynb.   
It is formatted to meet the input requirements of the Hugging Face implementation.  
### user_contacts.json
A mock user-data reference repository which contains user names, phone numbers, and any past requests.  
The chat function reads from and writes to this file.  
