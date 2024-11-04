# Named Entity Recognition (NER) with Llama 3.2

## Overview

This repository contains a **Named Entity Recognition (NER)** implementation using a **LLaMA 3.2** model using *HuggingFace*, specifically leveraging its autoregressive (decoder-only) architecture. The project demonstrates how to adapt a LLaMA model for NER tasks by disabling causal masking, enabling bidirectional attention, and applying **Low-Rank Adaptation (LoRA)** for fine-tuning. 

> [!IMPORTANT]
> This is a **showcase** project and thus not fully optimized or thoroughly tested.

## Purpose
Traditionally, encoder-only models like BERT have dominated NER tasks due to their ability to process input text bidirectionally, capturing rich contextual information. However, by removing the causal mask in LLaMA, we enable it to leverage bidirectional context while maintaining its strengths in generative tasks, making it a versatile solution for NER. Compared to encoder-only models like BERT, LLaMA offers several advantages:
* scalability: more effectively with larger datasets and parameters, enabling better performance on zero-shot and few-shot tasks. 
* its architecture can handle both generative and understanding tasks, making it more flexible. 

This makes LLaMA a (potentially) superior choice when both text generation and understanding are needed, especially in large-scale applications.

## Features

- **Model**: LLaMA 3.2 (1B) - a decoder-only transformer-based large language model (LLM).
- **Attention Mechanism**: Causal masking is disabled to allow bidirectional attention, suitable for NER tasks.
- **Optimization**:
  - **LoRA**: Low-Rank Adaptation is used to efficiently fine-tune the model with fewer trainable parameters.
  - **AdamW Optimizer**: The AdamW optimizer is used by default, as implemented in Hugging Face's Transformers library.
  - **Cosine Learning Rate Scheduler**: A cosine learning rate schedule is applied for smoother convergence.

## Dataset

* https://www.kaggle.com/datasets/juliangarratt/conll2003-dataset

## NER Tagging Structure

The **NER (Named Entity Recognition) tags** used in this project follow the **BIO tagging scheme**, which is commonly used in NER tasks to label entities in text. Here's a breakdown of what each tag means:

### **Tag Structure**
- **B-**: Indicates the beginning of a named entity.
- **I-**: Indicates that the token is inside a named entity but not at the beginning.
- **O**: Represents tokens that are not part of any named entity.

### **Entity Types**
- **PER**: Person (e.g., names of individuals)
- **ORG**: Organization (e.g., companies, institutions)
- **LOC**: Location (e.g., cities, countries, geographical regions)
- **MISC**: Miscellaneous entities that don't fall into the other categories (e.g., events, nationalities)
