# Customer Service bot using natural language generation and Hugging Face

The content in /cs-nlg is used to format a dataset to fine-tune a pretrained BERT model.  
It implements code that has been copied from Hugging Face to train a double-headed model which will simulate a conversation.


## How to use this code
### Using command line
NOTE: The approach is not recommended without access to a GPU.  
Copy the repo to your environment.  
Install the requirements.txt file. 
Change the working directory to cs-nlg
Run the train.py script to train a new model with a given dataset.  
    - This script can be run with a different dataset by changing the '--dataset_path' argument or by removing it entirely.
    - If the argument is removed, the script will reference the dataset hosted by Hugging Face.  
This will create a subfolder called /run/ where the trained model will be saved.  
Run interact.py to chat with the model.  
```
git clone https://github.com/rweddell/CustomerServiceBot-RW

cd /CustomerServicebot-RW/cs-nlg

pip install -r requirements.txt

python -m spacy download en

python ./CustomerServiceBot-RW/cs-nlg/hugging-face/train.py --dataset_path="cs_training_data.json" --n_epochs=20 --train_batch_size=4 --valid_batch_size=2 --max_history=4

python ./CustomerServiceBot-RW/cs-nlg/hugging-face/interact.py --model_checkpoint='<path/to/trained/model/>'
```

### Using a Colab notebook
This is the recommended approach if you don't have access to a GPU.   
Log into colab.research.google.com and open a new notebook or copy [cs-nlgbot.ipynb](https://github.com/rweddell/CustomerServiceBot-RW/blob/main/cs-nlg/cs-nlgbot.ipynb).  

Copy the following commands to a new cell and run.    
```
!git clone https://github.com/rweddell/CustomerServiceBot-RW  
!pip install -r /content/CustomerServiceBot-RW/cs-nlg/requirements.txt
!python -m spacy download en 
```
In a new cell, run the train.py script.  
    - This script can be run with a different dataset by changing the '--dataset_path' argument or by removing it entirely.
    - If the argument is removed, the script will reference the dataset hosted by Hugging Face.  
```
!python /content/CustomerServiceBot-RW/cs-nlg/hugging-face/train.py --dataset_path="/content/CustomerServiceBot-RW/cs-nlg/cs_training_data.json" --n_epochs=20 --train_batch_size=4 --valid_batch_size=2 --max_history=4  
```
The train.py script will create a new subfolder called 'run'.  
Within this folder is a subfolder that holds the trained model.   
In the last cell, run the interact.py script to chat with the model.  
```
# Example:
# !python  /content/CustomerServiceBot-RW/cs-nlg/hugging-face/interact.py --model_checkpoint='/content/runs/Apr04_18-29-05_70d03ffb9d9e_openai-gpt'

# Replace the --model_checkpoint argument with the path to your trained model
!python /content/CustomerServiceBot-RW/cs-nlg/hugging-face/interact.py --model_checkpoint='<path/to/trained/model/>'  
```  

### Creating your own dataset
The [make_dataset.ipynb](https://github.com/rweddell/CustomerServiceBot-RW/blob/main/cs-nlg/make_dataset.ipynb) can be used to format a given text file of conversations into the JSON format required by Hugging Face.  
The conversations have some requirements. Each conversation in the file should:  
    - be separated from other conversations with an empty line
    - begin with 'user' input, followed on the next line by the chatbot
    - should end with chatbot response 
Check [conversations.txt](https://github.com/rweddell/CustomerServiceBot-RW/blob/main/cs-nlg/conversations.txt) for example formatting.

The notebook also references a document of extra text for its 'distractor' requirement, which is essentially noise added to the input. The [financial_responses.txt](https://github.com/rweddell/CustomerServiceBot-RW/blob/main/cs-nlg/financial_responses.txt) can be used, but if you are making your own dataset, you may want to find your own distractors.

## About the files
### hugging-face/
These files were copied directly from Hugging Face's repository with some very small alterations.  
### conversations.txt
A collection of simulated conversations between a customer and a customer-service chatbot.   
The conversations begin with a statement from the customer and end with a reply from the chatbot.  
These conversations were collected from sessions run with the cs-bagofwords chatbot found in this repository.  
### cs_training_data.json
This is the json representation of the conversations.txt file after it has been passed through make_dataset.ipynb.   
It is formatted to meet the input requirements of the Hugging Face implementation.  
### cs_wordvectors.ipynb
Implement the scripts written by Hugging Face through a Jupyter notebook.  
This implementation allows the scripts to be run in the cloud such as in Colab.   
More information can be found in [this blogpost](https://medium.com/huggingface/how-to-build-a-state-of-the-art-conversational-ai-with-transfer-learning-2d818ac26313).   
### financial_responses.txt
A collection of responses from the FiQA financial question and answer dataset.  
They makeup the 'distractor' component of the dataset.   
The format of Hugging Face's input requires distractor statements in the input for one of the model heads in order to classify a potential response as in-context.   
### make_dataset.ipynb
Running the cells in this notebook will read two text files and formats the contents according to the requirements of Hugging Face.
### training_schema.
Shows the schema required by Hugging Face.
