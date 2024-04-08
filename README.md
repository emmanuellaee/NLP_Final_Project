# NLP_Final_Project
Question Answering System with RoBERTa
This repository contains code for building a Question Answering (QA) system using the RoBERTa model. The system is meant to be trained and evaluated on the Stanford Question Answering Dataset (SQuAD) version 2. As these files are quite large to upload to the repository, you can access them through the website: https://rajpurkar.github.io/SQuAD-explorer/. (file name: train-v2.0.json, dev-v2.0.json)

The dependencies include:
- Pytorch
- Transformers library
- Datasets library

To test this code: 
- clone repository
- install needed dependencies
- download the dataset files to your local drive
- upload to google colab

Preprocessing pipeline
- Data formatting: Firstly, the data is formatted into a dataframe separating the different features into separate columns
- Context and questions are tokenized using the pre-trained RoBERTa tokenizer
- There is a truncation parameter that has been set to a max length of 384 tokens for when the context exceeds this length to account for computational resources
- The offset mappings are also set to be returned with the tokenized input
- By iterating through the offset mappings, we are able to obtain the start and end positions of the answer span within the text
- Edge case: If answer is not contained within context, then positions are set to 0
- Additional dimension: The function 'convert_ans' is applied to the rows of the dataframe in order to extract the answer start positions and answer text span under answers dimension that is compatible with datasets library
- The data frame is then turned into a dataset object to allow compatibility with the map function for tokenizing the input 
