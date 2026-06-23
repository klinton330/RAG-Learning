# RAG

## What is RAG?

**Retrieval-Augmented Generation (RAG)** is a technique that combines:

1. **Retrieval** – Fetching relevant information from an external knowledge source.
2. **Augmentation** – Enriching the retrieved information with additional context or metadata.
3. **Generation** – Using the enriched information to generate a final response.

# Overview

## Retrieval-Augmented Generation (RAG) – Overview

### Introduction

Retrieval-Augmented Generation (RAG) is one of the most widely adopted architectures in Generative AI today. More than 80% of enterprise Generative AI applications use RAG to provide accurate, up-to-date, and domain-specific responses.

RAG enhances the capabilities of Large Language Models (LLMs) by allowing them to retrieve information from external knowledge sources before generating a response.

## What is RAG?

**Retrieval-Augmented Generation (RAG)** is a technique that combines:

1. **Retrieval** – Fetching relevant information from an external knowledge source.
2. **Augmentation** – Enriching the retrieved information with additional context or metadata.
3. **Generation** – Using the enriched information to generate a final response.

#### Definition

> RAG is a powerful technique that enhances AI language models by combining generation capabilities with external knowledge retrieval.

***

## Why Do We Need RAG?

Traditional LLMs are trained on a fixed dataset and have knowledge only up to their training cutoff date.

#### Example

Assume an LLM was trained on data available until **July 2023**.

**Question:**

> What is the latest AI news today?

The model cannot answer accurately because it does not have access to information beyond July 2023.

#### Solution

The LLM can be connected to an external source such as:

* Web Search API
* Database
* Internal Company Knowledge Base
* Documents Repository

The model retrieves current information from these sources and then generates a response.

***

## Real-World Example

Consider a company chatbot that answers employee-related questions.

#### User Query

> What is the latest leave policy of Company XYZ?

Since company policies are not part of the LLM's training data, the chatbot must retrieve the information from the company's knowledge repository.

The company documents are stored in a **Vector Database**.

The process becomes:

```
User Question
      ↓
Retriever
      ↓
Vector Database
      ↓
Relevant Documents
      ↓
LLM
      ↓
Generated Response
```

## Components of RAG

### 1. Retrieval (R)

Retrieval is the process of searching and fetching relevant information from an external knowledge source.

#### What happens?

1. User submits a query.
2. The query is converted into a vector (embedding).
3. The vector is compared against vectors stored in the Vector Database.
4. The most relevant documents are retrieved.

#### Example

Query:

> What is the latest leave policy?

Retrieved Document:

> Employees are entitled to 20 annual leave days and 10 sick leave days.

#### Retrieval Techniques

Common retrieval methods include:

* Similarity Search
* Semantic Search
* Vector Search
* Nearest Neighbor Search

These methods use similarity metrics to identify relevant content.

### 2. Augmentation (A)

Augmentation refers to enriching the retrieved information before sending it to the LLM.

Instead of passing only the retrieved text, additional metadata can be included.

#### Retrieved Content

```
Revenue increased by 10%
```

#### Augmented Content

```
Text: Revenue increased by 10%
Source: Tesla Annual Report
Date: 2025
Document Type: Financial Report
```

#### Benefits of Augmentation

* Improves response accuracy
* Provides source attribution
* Adds context
* Reduces hallucinations
* Enables traceability

The enriched content becomes the context provided to the LLM.

### 3. Generation (G)

Generation is the process where the LLM creates a human-readable response using:

* User query
* Retrieved documents
* Augmented metadata

#### Example

**Context Provided to LLM**

```
Revenue increased by 10%
Source: Tesla Annual Report
Date: 2025
```

**Generated Response**

> According to Tesla's 2025 Annual Report, the company's revenue increased by 10% compared to the previous year.

The LLM summarizes and presents the information in a natural language format.

## What is a Vector Database?

A Vector Database stores information in the form of numerical vectors (embeddings).

Instead of traditional keyword matching, it enables semantic similarity searches.

Popular Vector Databases include:

* Pinecone
* Weaviate
* Chroma
* Milvus
* Qdrant

## High-Level RAG Workflow

```
Documents
    ↓
Document Processing
    ↓
Chunking
    ↓
Embedding Generation
    ↓
Vector Database Storage
    ↓

User Query
    ↓
Query Embedding
    ↓
Similarity Search
    ↓
Retrieve Relevant Chunks
    ↓
Augment Context
    ↓
LLM
    ↓
Generated Response
```

## Three Major Phases of RAG Architecture

### 1. Document Ingestion Phase

This phase prepares data for retrieval.

Activities include:

* Collecting documents
* Data cleaning
* Document chunking
* Embedding generation
* Storing embeddings in a Vector Database

#### Output

A searchable knowledge base.

### 2. Query Processing Phase

This phase handles user questions.

Activities include:

* Receiving user query
* Converting query into embeddings
* Performing similarity search
* Retrieving relevant documents

#### Output

Relevant context for the LLM.

### 3. Generation Phase

This phase generates the final answer.

Activities include:

* Augmenting retrieved content
* Passing context to the LLM
* Generating natural language response

#### Output

Final answer returned to the user.

## Traditional LLM vs RAG

| Traditional LLM                    | RAG-Based System                        |
| ---------------------------------- | --------------------------------------- |
| Uses only training data            | Uses training data + external knowledge |
| Knowledge becomes outdated         | Can access latest information           |
| May hallucinate                    | More accurate responses                 |
| No access to company-specific data | Can use private organizational data     |
| Closed-book exam                   | Open-book exam                          |

## Key Benefits of RAG

#### Up-to-Date Information

Accesses current information from external sources.

#### Reduced Hallucination

Responses are grounded in retrieved documents.

#### Domain-Specific Knowledge

Can answer questions using company documents and proprietary data.

#### Source Traceability

Responses can reference the original document source.

#### Cost Effective

No need to retrain the LLM whenever documents change.

## Summary

RAG (Retrieval-Augmented Generation) is a framework that enhances LLMs by combining external knowledge retrieval with response generation.

The process consists of:

1. **Retrieval** – Fetch relevant information from a Vector Database.
2. **Augmentation** – Enrich retrieved information with metadata and context.
3. **Generation** – Use the enriched context to generate accurate, natural-language responses.

This architecture enables AI systems to provide accurate, current, and organization-specific answers, making it the foundation of most modern enterprise Generative AI applications.