# RAG Pipeline

This repository contains the RAG (Retriever-Augmented Generation) pipeline designed to process documents, retrieve relevant information, and generate answers to user queries. This pipeline serves as a foundation for advanced RAG research and module building. The pipeline works in five main steps:

1. **Preprocess**: Document chunking and database building to prepare the knowledge base for retrieval.
2. **Retrieval**: Querying a database of documents to find the most relevant content using hybrid retrieval methods, including keyword matching, semantic similarities, and more advanced retrieval techniques.
3. **Rerank**: Applying advanced reranking algorithms to reorder the retrieved documents, enhancing the quality and relevance of the retrieved results.
4. **Generate**: Producing a coherent and contextually relevant answer by leveraging the reranked documents along with the original question.
5. **Evaluation**: Assessing the quality of the generated answers using multiple reference-based metrics, providing insights into the effectiveness of the retrieval and generation stages.

## Features

- Runs locally on a personal laptop.
- Document preprocessing and chunking to handle large texts.
- Integration with Haystack for vector database building, advanced search, and retrieval capabilities.
- Hybrid retrieval methods, including keyword search and vector-based retrieval (embedding and dense passage retrievers).
- Reranking to improve retrieval quality before answer generation.
- Evaluation of generated answers using multiple metrics for comprehensive analysis.

## Evaluation Metrics

The performance of the pipeline is evaluated using three types of reference-based metrics:

1. **Overlap-Based Metrics**:
   - **ROUGE-1**: Measures unigram overlap.
   - **ROUGE-L**: Captures the longest common subsequence, focusing on text structure and coherence.

2. **Similarity-Based Metrics**:
   - **BERT Similarity**: Cosine similarity using BERT embeddings.
   - **GPT Similarity**: Cosine similarity using GPT embeddings.

3. **Quantitative-Based Metrics**:
   - **BLEU Score**: Measures n-gram precision.
   - **Entailment Score**: Uses an NLI model to assess logical consistency and factual correctness.

## Configurations

1. **Tokenization**:
   - Model: `bert-base-uncased`

2. **Retriever**:
   - Embedding Retriever: `bert-base-uncased`
   - Dense Passage Retriever:
     - Query Embedding Model: `dpr-question_encoder-single-nq-base`
     - Passage Embedding Model: `dpr-ctx_encoder-single-nq-base`
   - Keyword Retriever: `bm25`

3. **Reranker**:
   - Model: `bert-large-uncased-whole-word-masking-finetuned-squad`

4. **Generation**:
   - Model: `t5-large`

5. **Evaluation**:
   - BERT Similarity: `bert-base-nli-mean-tokens`
   - GPT Similarity: `sentence-transformers/all-MiniLM-L6-v2`
   - Entailment: `roberta-large-mnli`

## Prerequisites

- Python 3.9+
- Haystack
- Transformers
- PyTorch
- FAISS for efficient similarity search
- pandas
- spacy
- seaborn
- matplotlib

## Installation

Clone the repository and install the required Python packages:

\`\`\`bash
pip install -r requirements.txt
\`\`\`

## Usage

Run the main script to start the pipeline:

\`\`\`bash
python rag_pipeline.py
\`\`\`

### 3. Folder Structure

\`\`\`plaintext
RAG_Pipeline/
├── data/                                 # Data files
│   ├── README.md                         # Documentation and instructions to download data
│   ├── data_prep.ipynb                   # Notebook for document collection and preparation
├── rag/                                  # RAG pipeline components
│   ├── generator.py                      # Script for generating answers
│   ├── hybrid_retrieval.py               # Script for setting up multiple retrievers and databases
│   ├── preprocess.py                     # Script for document chunking
│   ├── rerank.py                         # Script for reranking retrieved documents
│   ├── rag_pipeline.py                   # Main pipeline driver script
├── requirements.txt                      # Required Python packages
├── README.md                             # Documentation of the RAG pipeline and evaluation
\`\`\`

## Work-in-Progress and Research Directions

- **Selective Text-Based Optimization**: Maximize relevance and diversity of selected documents.
- **Advanced Reranking**: Investigate reranking algorithms/models like reciprocal rank fusion or cross-encoder.
- **State-of-the-Art Models**: Integrate the latest models for both retrievers and generators.
- **RAT**: Combine RAG and CoT to eliminate hallucinations and improve answer quality.
- **Knowledge Graph (KG) guided RAG**: Focus on building complete and accurate knowledge graphs instead of relying solely on retrieval.
"""
