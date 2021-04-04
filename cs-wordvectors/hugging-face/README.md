# About these files
These files in the /hugging-face folder were copied directly from [HuggingFace's repository](https://github.com/huggingface/transfer-learning-conv-ai).  
Most of the files are unaltered, with the exception of train.py.  

In train.py, on lines 76, 96, and 106, the string "valid" has been changed to "validate" to correct what seems to be a typo.


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



