# Customer Service bot using word vectors and Hugging Face

The content in /cs-wordvectors is used to format a dataset to finetune a pretrained BERT model.  
It implements code from Hugging Face to train a double-headed model which will simulate a conversation.


## About the files
### conversations.txt
A collection of simulated conversations between a customer and a customer-service chatbot.   
The conversations begin with a statement from the customer and end with a reply from the chatbot.  
These conversations were collected from sessions run with the cs-bagofwords chatbot found in this repository.  
### cs_training_data.json
This is the json representation of the conversations.txt file after it has been passed through make_dataset.ipynb.   
It is formatted to meet the input requirements of the Hugging Face implementation.  
### cs_wordvectors.ipynb
Demonstration of the logic implemented by Hugging Face.   
More information can be found in [this blogpost](https://medium.com/huggingface/how-to-build-a-state-of-the-art-conversational-ai-with-transfer-learning-2d818ac26313).   
### financial_responses.txt
A collection of responses from a financial question and answer dataset.  
They a form of filler in the dataset which are known as 'distractors'.    
The format of Hugging Face's input requires distractor statements included in the input for one of the heads of the model in order to classify a potential response as in-context.   
### make_dataset.ipynb
Running the cells in this notebook will read two text files and formats the contents according to the requirements of Hugging Face.
### training_schema.
Shows the schema required by Hugging Face.