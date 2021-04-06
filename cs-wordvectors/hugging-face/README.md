# About these files
These files in the /hugging-face folder were copied directly from [Hugging Face's repository](https://github.com/huggingface/transfer-learning-conv-ai).  
The files are unaltered, with the exception of train.py.  

In train.py, on lines 76, 96, and 106, the string "valid" has been changed to "validate" to correct what seems to be a typo.  
It will otherwise cause an exception to be raised as a KeyError.




Line 76
```
--- datasets = {"train": defaultdict(list), "valid": defaultdict(list)}
+++ datasets = {"train": defaultdict(list), "validate": defaultdict(list)}
```

Line 96
```
--- tensor_datasets = {"train": [], "valid": []}
+++ tensor_datasets = {"train": [], "validate": []}
```

Line 106
```
--- train_dataset, valid_dataset = TensorDataset(*tensor_datasets["train"]), TensorDataset(*tensor_datasets["valid"])}
+++ train_dataset, valid_dataset = TensorDataset(*tensor_datasets["train"]), TensorDataset(*tensor_datasets["validate"])}
```


Additionally, line 26 was changed to include custom tokens which I am testing in hopes that they will represent a customer's first and last name.

```
--- ATTR_TO_SPECIAL_TOKEN = {'bos_token': '<bos>', 'eos_token': '<eos>', 'pad_token': '<pad>',
                         'additional_special_tokens': ['<speaker1>', '<speaker2>', '<f_name>', '<l_name>']}  
+++ ATTR_TO_SPECIAL_TOKEN = {'bos_token': '<bos>', 'eos_token': '<eos>', 'pad_token': '<pad>',
                         'additional_special_tokens': ['<speaker1>', '<speaker2>', '<f_name>', '<l_name>']}  
```
