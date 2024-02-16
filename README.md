# RAG Bot Report

## Overview

This report provides a comprehensive overview of the RAG Bot developed by Muhammad Hasham Ul Haq. The bot is designed to recommend Urdu stories based on user queries using a combination of a pre-trained DistilBERT model, mini-Language Models (mini-LM), and Annoy Index.

## Data Preprocessing

### Dataset

The Urdu Stories dataset is loaded from 'urdu_stories.csv'. A new column 'Split_ID' is created for categorizing the dataset into training and validation sets. The dataset is then split into 80% training and 20% validation sets.

### Tokenization

The DistilBERT Tokenizer is used to tokenize the Urdu stories. The tokenized data is organized into a custom UrduDataset class, facilitating easy integration with PyTorch DataLoader.

## Training DistilBERT Model

A pre-trained DistilBERT model for sequence classification is fine-tuned on the training dataset. The model is trained for three epochs using AdamW optimizer.

## Training mini-Language Models (mini-LM)

Mini-LMs are created for each split in the dataset to capture split-specific language patterns. Each mini-LM consists of a DistilBERT model and a linear layer. These models are trained for three epochs on split-specific datasets.

## Annoy Index

An Annoy Index is created for each mini-LM to efficiently retrieve similar embeddings. Embeddings are generated using mean pooling, and these embeddings, along with relevant information, are stored in Annoy Index files.

## Usage

### Running the RAG Bot

1. Install dependencies: `transformers`, `accelerate`, `annoy`.
2. Execute the provided code to train the DistilBERT model, mini-LMs, and create Annoy Index files.
3. Load the trained mini-LM and Annoy Index for the corresponding split.
4. Use the `get_query_embeddings` function to obtain embeddings for a user query.
5. Use the `query_vector_database` function to find similar splits and distances.
6. Display recommendations based on the obtained results.

## Conclusion

The RAG Bot effectively combines pre-trained models and mini-LMs with Annoy Index to provide personalized Urdu story recommendations. Future work could involve integrating Speech-to-Text (STT) and Text-to-Speech (TTS) modules to enhance the user experience. The modular structure of the code facilitates easy expansion and integration of additional functionalities.
