# Customer Service bot using word vectors and Hugging Face

The content in /cs-wordvectors is used to format a dataset to finetune a pretrained BERT model.  
It implements code that has been copied from Hugging Face to train a double-headed model which will simulate a conversation.


## How to use this code
### Using command line
NOTE: The approach is not recommended without access to a GPU.  
Copy the repo to your environment.  
Install the requirements.txt file. 
Change the working directory to cs-wordvectors
Run the train.py script to train a new model with a given dataset.  
This will create a subfolder called /run/ where the trained model will be saved.  
Run interact.py to chat with the model.  
```
git clone https://github.com/rweddell/CustomerServiceBot-RW

cd /CustomerServicebot-RW/cs-wordvectors

pip install -r requirements.txt

python ./hugging-face/train.py --dataset_path="cs_training_data.json" --n_epochs=1 --train_batch_size=1 --valid_batch_size=3 --max_history=4

python ./hugging-face/interact.py --model_checkpoint='<path/to/trained/model/>'
```
### Using a Colab notebook
This is the recommended approach if you don't have access to a GPU.   
Log into colab.research.google.com and open a new notebook.  
Copy the following commands to a new cell and run.    
```
!git clone https://github.com/rweddell/CustomerServiceBot-RW  
!pip install -r /content/CustomerServiceBot-RW/cs-wordvectors/requirements.txt
!python -m spacy download en 
```
In a new cell, run the train.py script.  
```
!python ./hugging-face/train.py --dataset_path="cs_training_data.json" --n_epochs=3 --train_batch_size=3 --valid_batch_size=3 --max_history=4  
```
The train.py script will create a new subfolder called 'run'.  
Within this folder is another folder that holds the trained model.   
In the last cell, run the interact.py script to chat with the model.  
```
# Example:
# !python  /content/CustomerServiceBot-RW/cs-wordvectors/hugging-face/interact.py --model_checkpoint='/content/runs/Apr04_18-29-05_70d03ffb9d9e_openai-gpt'

# Replace the --model_checkpoint argument with the path to your trained model
!python /content/CustomerServiceBot-RW/cs-wordvectors/hugging-face/interact.py --model_checkpoint='<path/to/trained/model/>'  
```  

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
A collection of responses from a financial question and answer dataset.  
They make a component in the dataset which are known as 'distractors'.    
The format of Hugging Face's input requires distractor statements included in the input for one of the heads of the model in order to classify a potential response as in-context.   
### make_dataset.ipynb
Running the cells in this notebook will read two text files and formats the contents according to the requirements of Hugging Face.
### training_schema.
Shows the schema required by Hugging Face.