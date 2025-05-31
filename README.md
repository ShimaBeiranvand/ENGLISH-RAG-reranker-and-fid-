# ENGLISH-RAG-reranker-and-fid-

Project Title:
   English RAG using reranker and FID technique

Description:
In this project we are trying to answer some questions based on our dataset (trying to retrieve the most related document by reranker technique)
and using a generator which recieves the question and the document(s) and generates the answer (using FID technique)

Installation and Usage:

1.download dataset 
2.pip install os , re , sklearn , nltk , transformers , torch
3.installing every other special library is written as code in the jupyter notebook
4.run the code!!!

Methodology:

This project implements a dual-pipeline approach for document-based question answering. Below is the structured workflow:
1. Document Processing Pipeline
1.1 Data Preparation

    PDF Extraction: Raw text extracted from PDF documents

    Text Preprocessing:

        Lowercasing

        White space normalization (removal of extra spaces/tabs)

1.2 Retrieval-Augmented QA System

    Document Ranking:
    find_top_related_docs() function identifies top 3 relevant documents

    Text Chunking:
    string_chunker() processes selected documents into manageable segments

    Answer Generation:

        Selects top document & chunk using similarity ranking

        Employs deepset/roberta-base-squad2 model in QA pipeline

        Outputs final answer using question + most relevant text chunk

# Simplified workflow
answer = qa_pipeline(question=user_query, context=top_chunk)

2. Fusion-in-Decoder (FiD) Approach
2.1 Multi-Document Fusion

    Retrieves top 3 documents using initial ranking

    Constructs composite input structure:
    ['question doc1', 'question doc2', 'question doc3']

2.2 Attention-Based Generation

    Implements custom attention masking

    Processes concatenated inputs through transformer generator

    Decodes final answer using fused document context

# FiD processing example
generated_tokens = model.generate(input_ids, attention_mask=mask)
answer = tokenizer.decode(generated_tokens)

3. Evaluation Framework

    Metric: ROUGE (Recall-Oriented Understudy for Gisting Evaluation)

    Comparative Analysis:

        Scores for retriever-based answers vs FiD-generated answers

        Precision/recall analysis for answer quality assessment

Contributing:

Thank you for your interest in contributing to this project!
If you have any suggestions, find bugs, or want to improve the code, please feel free to reach out.

You can contact me at: shimabeiranvand5@gmail.com

I would be grateful for any feedback, ideas, or contributions you can provide to help improve this project.

Thank you!!!
