# CustomerServiceBot-RW
Example customer service chatbots of various complexities and implementations

## Description
This project uses python/jupyter to train and interact with chatbots. The use case is in the form of a customer service agent at a bank.

In this repo are two different implementations. One uses a model which returns canned responses based on the classification of the intent of user input. The second uses natural language generation to build a response to user input based on conversation history. 

## Thought process and development
The original intent of this project was to explore the viability of using natural language generation in a mock production-level chatbot. At its heart, the interaction between a user and a chatbot is a conversation. The chatbot needs to collect the user's intent and output a response. 

At the time of this writing, the state-of-the-art for a conversational chatbot is [created by Hugging Face](https://convai.huggingface.co/), which uses a double-headed BERT model and a specifically formatted dataset. The dataset holds a personality as well as a ordered sequence of chat history. The chat history is integrated with the persona to build responses.  

Natural Language Generation (NLG) is a process by which a linguistically realistic sequence of words is constructed using a seed of text, such as a question or a greeting. The risk with NLG is that it is, at least at this point in time, an inherintly unguaranteeable process. There is always a possibiility that the output does not make sense linguistically or contextually.

Below are two example conversations generated from a HuggingFace model fine-tuned on a dataset created to represent conversations between a chatbot and a banking customer. The files in [/cs-nlg](https://github.com/rweddell/CustomerServiceBot-RW/tree/main/cs-nlg) were used to create this output from a Colab notebook.

```
You: hi can I open a new account?
Bot: youre trying to open a new account. is that right?
You: yes
Bot: i can log a request. please give me your first and last name.
You: my name is sandy beach
Bot: a representative of botbank. is there anything else i can help with?
You: can I open a new account?
Bot: a request has been logged for your account. is there anything else i can help with?
You: can you tell me my account balance?
Bot: thank you. a request has been logged for your account. what else i can help with?
You: account balance
Bot: you want to check your account balance. is that correct?
You: yes
Bot: thank you. i just need to ask a few questions. please give me your first and last name
You: my name is sandy beach
Bot: your account balance is $ 354456. is there anything else i can help with?
You: no that's all
Bot: thank you for using botbank.

You: hours of operation
Bot: all botbank locations are open 7am to 4pm monday through friday! what else i can help
You: can I open a new account?
Bot: you want to open an account. is that right?
You: yes
Bot: thank you. i just need to ask a few questions. please give me your first and last name
You: joe dirt
Bot: thank you.
You: did you open a new account?
Bot: you are trying to open a new account. is that right?
You: yes
Bot: i can log a request. please give me your first and last name.
You: joe dirt
Bot: glad i could help. thanks for choosing botbank have a nice day.
```

It is clear that the output is mostly in-context, but would not result in a satisfying customer experience. The customer had to repeat their statements, and the responses from the chatbot were often vague and unhelpful. At best it seems like talking to a person who is mostly focused on something else.  

This is in contrast to a model which uses canned responses. This type of model classifies the user's intent, asks for clarification, and outputs a pre-written response. The result is extremely effective, but is the conversational equivalent of filling out paperwork. The following result was obtained using the files within [/cs-cannedresponse](https://github.com/rweddell/CustomerServiceBot-RW/tree/main/cs-cannedresponse).

```
Bot: Hi there, how can I help?
You: Open a new account
Bot: You are trying to open an account. Is that correct?
You: Yes
Bot: Thanks for the confirmation.
Bot: You will need to speak with a representative, but I can log a request to speed up the process.
Bot: Please give me your first and last name.
You: My name is Taylor Suit
Bot: Your first and last name is Taylor Suit. Is that correct?
You: Correct
Bot: Thank you.
Bot: Please give me your phone number.
You: 3847394742
Bot: Your phone number is 3847394742. Is that correct?
You: Yes
Bot: Thanks.
Bot: A request has been logged for Taylor Suit to 'open account'
Bot: Is there anything else I can help with?
You: What are the hours of operation?
Bot: All BotBank locations are open 7am-4pm Monday-Friday!
Bot: Is there anything else I can help with?
You: No that's all
Bot: Glad I could help. Thanks for choosing BotBank! Have a nice day.
```

The result is that NLG on its own is not viable when a user is seeking specific information or a specific interaction. Specific outputs based on user intents cannot be guaranteed. However, results may be improved with a much larger training set, and longer training times.
