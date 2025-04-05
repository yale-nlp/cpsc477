---
layout: page
permalink: /homework/
title: Homework Assignments
---

All homeworks should be submitted through Gradscope.


## Homework 3

Note: This homework requires training models. 
We would recommend starting early as last minute issues with GPUs/availability are not uncommon.

### Part 1: Fine-tuning language models with preference feedback (80 points)

In this part, you will implement a training pipeline for language models and fine-tune them with preference feedback using the Direct Preference Optimization (DPO) framework. You will also evaluate the performance of the fine-tuned models on a text classification task.
The detailed instructions are provided in the Colab notebook.

Access the Colab Notebook Here: [Colab Notebook](https://colab.research.google.com/drive/1qdOZmacmSIlOQWj1oRI4l41DPZspYrh-?usp=sharing)

The notebook is self-contained and will guide you through the process of implementing DPO and training a model with it.

### Part 2: Implementing LoRA from scratch (70 points)

The objective of this part is to implement the LoRA model from scratch.

You will be using the Hugging Face `transformers` library to load the model and the dataset.
Then you will be modifying a `Roberta` pre-trained model to make it a LoRA model.
Then you will be training the model on a small sentiment analysis dataset and investigate the performance of the model.

Download the Google Colab notebook from the following link: [Download](https://colab.research.google.com/drive/14KxwtxPe6_72-x8pOalTpUkpxtCrNv08?usp=sharing).

The notebook is self-contained and will guide you through the process of implementing the LoRA model from scratch.

Note: This part might take a while to train (about 25 minutes on T4 gpus).
So I would recommend either running it on a local server or on HPC cluster.
And please start early.

### Part 3: Implementing a retrieval pipeline for a RAG system (50 points)

In this part, you will be implementing a retrieval pipeline for a RAG system.

You will be using and implementing an encoder model with dense embeddings and a dense retriever.


Download the Google Colab notebook from the following link: [Download](https://colab.research.google.com/drive/1q_2IBrEXgh4j0rDwCgwsfj2wr4v88T3U?usp=sharing).

The notebook is self-contained and will guide you through the process of implementing the LoRA model from scratch.



## Homework 2

### Part 1: Implementing a transformer model (50 points)

In this part, your goal is to design and implement a Transformer-based model. You are expected to gain a deeper understanding of the inner workings of the Transformer by building its core components from scratch.

Download the Google Colab notebook from the following link: [Download](https://drive.google.com/file/d/1ZxsE5lvOdtodmNI_eS86i612ytxTRb6u/view?usp=sharing).


### Part 2: Text generation and decoding (50 points)

n this part, you will apply your Transformer model for sequence generation. This will be a task on text summarization in which you will explore using an off-the-shelf language model, and evaluation methods. This also focuses on experimenting with and evaluating different decoding strategies for text generation.

Download the Google Colab notebook from the following link: [Download](https://drive.google.com/file/d/1ZVRMaZv4nzoGE1LhIBGZH3Eel5UyCHFw/view?usp=sharing).

## Homework 1

### Part 1: Hands-on excercise - Implementing sparse representations (50 points)

In this homework, your goal is to implement sparse word and document representations. Sparse representations are crucial in many natural language processing tasks, particularly when working with high-dimensional data like text.

You will need to log in to colab with your Yale account.
Then you can copy the notebook to your own account and start working on that. 

You will be completing parts indicated with 
```
    #
    # % -- Your Implementation -- %
    #
```

Or `# TODO: Implement`. 

Then you will be submitting the completed notebook with all the outputs.

Please see the instructions and the notebook here: [Colab-1](https://colab.research.google.com/drive/1uIi5UvVCrAzsYJZ3CPzwF3coY3XM5lcu?usp=sharing).

### Part 2: Handout (20 points) 

Download the homework handout from the following link: [Download](https://yaleedu-my.sharepoint.com/:b:/g/personal/arman_cohan_yale_edu/EcwlF76Mgf5EvZf8jMUwR40BZG-9eBMtfuzdj4-jif81oA?e=bivaWM).

For this part, you need to complete the homework in LaTeX and return the pdf solution. Further instructions are provided in the pdf.

### Part 3: Hands-on excercise - Implementing the Word2Vec model (50 points)

The third part is implementation of a `Word2Vec` SkipGram model from scratch.
A Colab notebook is provided to guide you through the process of implementing the model from scratch and training it on a toy data sample.

Then you will be submitting the completed notebook with all the outputs.

Please see the instructions and the notebook here: [Colab-2](https://colab.research.google.com/drive/1f9RIb0nPQ1RMaibeiIFVqmA1M8bft2_N?authuser=2).