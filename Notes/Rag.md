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

# RAG-Detailed

## Retrieval-Augmented Generation (RAG) – Detailed

### Retrieval-Augmented Generation (RAG) – Detailed Documentation

#### Overview

**Retrieval-Augmented Generation (RAG)** is an AI architecture that combines the power of Large Language Models (LLMs) with external knowledge sources such as vector databases. Instead of relying only on the information learned during training, RAG retrieves relevant information from a knowledge repository and provides it to the LLM before generating a response.

The RAG process consists of three key stages:

1. **Retrieval**
2. **Augmentation**
3. **Generation**

***

### 1. RAG Workflow

#### 1.1 Retrieval

When a user submits a query, the system performs a similarity search against a vector database to find the most relevant information.

**Key Activities:**

* User submits a query.
* Query is converted into vector embeddings.
* Similarity search is performed in the vector database.
* Relevant documents or knowledge chunks are retrieved.

**Purpose:**

To provide the LLM with context that is directly related to the user's question.

***

#### 1.2 Augmentation

After retrieval, the retrieved information is enriched with additional context and metadata.

**Examples of Metadata:**

* Document source
* Version information
* Creation date
* Department ownership
* Confidence score

**Purpose:**

To improve response accuracy and provide more reliable context to the LLM.

***

#### 1.3 Generation

The retrieved and augmented content is passed to the LLM as contextual information.

The LLM then:

* Analyzes the provided context.
* Summarizes relevant information.
* Generates a final response for the user.

**Purpose:**

To produce accurate and context-aware responses.

***

### 2. Why RAG Matters

Traditional LLMs are limited to the information available during their training period. They cannot automatically access:

* Latest company policies
* Recent product updates
* Internal documentation
* Real-time business information

RAG addresses this limitation by allowing LLMs to retrieve up-to-date information from external data sources.

#### Benefits of RAG

* Improved accuracy
* Reduced hallucinations
* Access to current information
* No need for frequent model retraining
* Better enterprise knowledge management
* Lower operational costs

***

### 3. Chef Analogy for Understanding RAG

Consider a restaurant chef as an LLM.

#### Scenario 1: Chef Without Knowledge

A customer orders a foreign dish.

The chef:

* Has never learned the recipe.
* Attempts to guess the preparation method.
* Produces an incorrect dish.

This resembles **LLM hallucination**, where the model generates information without sufficient knowledge.

***

#### Scenario 2: Chef Says "I Don't Know"

The chef admits not knowing the recipe.

Similarly, an LLM may fail to provide an answer when it lacks relevant information.

***

#### Scenario 3: Chef Uses Recipe Books

The chef:

1. Searches recipe books.
2. Finds the correct recipe.
3. Follows the instructions.
4. Prepares the dish successfully.

In a RAG system:

| Restaurant Example | RAG Equivalent     |
| ------------------ | ------------------ |
| Chef               | LLM                |
| Recipe Books       | Vector Database    |
| Searching Recipe   | Retrieval          |
| Recipe Details     | Context            |
| Final Dish         | Generated Response |

This enables the LLM to generate accurate responses based on retrieved knowledge.

***

### 4. Role of Vector Databases

A vector database stores information in the form of embeddings (numerical vector representations).

#### Data Stored

* Text documents
* PDFs
* Images
* Audio files
* Videos
* Knowledge articles
* Company policies

#### Process

1. Data is converted into embeddings.
2. Embeddings are stored in a vector database.
3. User queries are converted into embeddings.
4. Similarity search identifies matching content.
5. Relevant content is retrieved and passed to the LLM.

#### Common Vector Databases

* Pinecone
* Weaviate
* Milvus
* Chroma
* FAISS

### 5. Customer Support Use Case

#### Without RAG

**Customer Question:**

> What is your return policy for items purchased during the Black Friday sale?

**LLM Response:**

> Most companies generally offer a 30-day return policy, but policies may vary.

#### Problems

* Generic response
* Not company-specific
* Potentially inaccurate
* Low customer satisfaction

***

#### With RAG

**Workflow:**

1. Query received.
2. Search performed against company policy documents.
3. Relevant policy retrieved.
4. Context passed to LLM.
5. Response generated.

**Example Response:**

> According to our current policy document (Version 3.2), Black Friday purchases are eligible for a 60-day return window until January 31.

#### Benefits

* Company-specific information
* Higher accuracy
* Better customer experience
* Reduced support workload

### 6. Hallucination Reduction

#### What is Hallucination?

Hallucination occurs when an LLM:

* Generates incorrect information.
* Makes assumptions without supporting data.
* Produces confident but inaccurate answers.

#### Example

An LLM without access to company data may invent policies or procedures.

#### How RAG Helps

RAG provides factual information from trusted sources before response generation.

Result:

* Reduced hallucination
* Improved reliability
* Better trustworthiness

### 7. Enterprise Benefits of RAG

#### Cost Savings

Organizations can leverage existing knowledge repositories instead of continuously retraining or fine-tuning models.

#### Faster Knowledge Access

Employees can instantly retrieve information from:

* Policies
* Manuals
* Knowledge bases
* Research documents

#### Improved Decision Making

Users receive answers grounded in company-approved information.

#### Scalability

New documents can be added to the vector database without retraining the model.

### 8. Real-World Applications of RAG

#### Customer Support

* Policy lookup
* Product information
* Troubleshooting assistance

#### Financial Services

* Research assistance
* Market analysis
* Compliance document retrieval

#### Healthcare

* Clinical knowledge retrieval
* Medical guideline lookup
* Compliance support

#### Legal

* Contract analysis
* Policy interpretation
* Regulation search

#### Enterprise Knowledge Management

* Internal documentation search
* HR policy assistance
* IT support automation

***

### 9. High-Level RAG Architecture

```
User Query
     │
     ▼
Embedding Model
     │
     ▼
Vector Database
(Similarity Search)
     │
     ▼
Relevant Documents Retrieved
     │
     ▼
Augmentation
(Add Metadata & Context)
     │
     ▼
Large Language Model (LLM)
     │
     ▼
Generated Response
     │
     ▼
User
```

***

### Conclusion

Retrieval-Augmented Generation (RAG) enhances traditional LLMs by integrating them with external knowledge sources. Through Retrieval, Augmentation, and Generation, RAG delivers accurate, up-to-date, and context-aware responses while reducing hallucinations and eliminating the need for frequent model retraining. This makes RAG a preferred architecture for enterprise AI applications such as customer support, knowledge management, finance, healthcare, and legal systems.
# Prompt Engineering vs Fine-Tuning vs RAG

## Introduction

When building AI applications using Large Language Models (LLMs), three common approaches are used:

1. **Prompt Engineering**
2. **Fine-Tuning**
3. **Retrieval-Augmented Generation (RAG)**

Many people are confused about when to use each approach and how they differ. This document explains their working principles, advantages, disadvantages, and ideal use cases.

## 1. Prompt Engineering

### What is Prompt Engineering?

Prompt Engineering is the process of providing clear instructions to a pre-trained LLM to guide its behavior and generate desired responses.

The underlying model remains unchanged. Only the prompt (instruction) is modified.

#### Example

**Prompt:**

> Act as a professional chef and provide cooking recipes.

**User Query:**

> How do I prepare pizza?

The LLM generates the answer by following the instructions provided in the prompt.

### How Prompt Engineering Works

1. A user provides a structured prompt.
2. The prompt contains instructions and context.
3. The LLM processes the prompt.
4. The LLM generates a customized response.

#### Key Characteristics

* Requires clear instructions.
* Context should be well defined.
* No modification of model parameters.
* Uses the same pre-trained model.

### Advantages

#### Easy to Use

No machine learning expertise is required.

#### Quick Results

Responses are generated immediately.

#### No Training Cost

No additional model training is necessary.

#### Works with Any LLM

Can be used with models such as:

* GPT
* Gemini
* Llama
* Claude

### Limitations

#### Limited Knowledge

The model can only answer based on its pre-trained knowledge.

#### Inconsistent Responses

Small prompt changes can produce different outputs.

#### Token Limit Restrictions

Long prompts may exceed the model's context window.

#### Cannot Add New Knowledge

Prompts cannot permanently teach the model new information.

### Best Use Cases

* Small-scale AI applications
* Quick prototyping
* General-purpose chatbots
* Content generation
* Generic question-answering systems

#### Not Recommended For

* Company-specific assistants
* Domain-specific knowledge systems
* Applications requiring highly accurate business data

## 2. Fine-Tuning

### What is Fine-Tuning?

Fine-Tuning is the process of retraining a pre-trained LLM using custom domain-specific data.

This permanently modifies the model's weights so it learns specialized behavior and knowledge.

### Example

A company wants an AI assistant that always responds according to its brand guidelines.

Instead of relying on prompts, the company trains the model using its own data.

The resulting model behaves according to company-specific requirements.

### How Fine-Tuning Works

#### Step 1: Prepare Domain Data

Collect organization-specific training data.

Examples:

* Legal documents
* Medical records
* Internal company FAQs
* Product manuals

#### Step 2: Train the Base Model

Train the LLM using the custom dataset.

#### Step 3: Update Model Weights

The training process modifies model parameters.

#### Step 4: Create a Specialized Model

A new fine-tuned model is produced for the specific domain.

### Advantages

#### Deep Domain Knowledge

Provides expertise in a specific field.

#### Consistent Behavior

Produces predictable responses.

#### Learns Custom Styles

Can learn:

* Writing styles
* Brand tone
* Response formats

#### High Accuracy

Performs well for specialized tasks.

### Limitations

#### Expensive

Requires GPU resources and training infrastructure.

#### Requires Expertise

Needs AI and machine learning knowledge.

#### Retraining Needed

Model must be retrained whenever data changes.

#### Time-Consuming

Training large models can take significant time.

### Best Use Cases

* Legal assistants
* Medical assistants
* Financial advisory systems
* Brand-specific chatbots
* Specialized enterprise AI applications

#### Ideal When

* High accuracy is critical.
* Consistent behavior is required.
* Large amounts of domain-specific data are available.

## 3. Retrieval-Augmented Generation (RAG)

### What is RAG?

Retrieval-Augmented Generation (RAG) combines an LLM with an external knowledge source.

Instead of training the model with new data, RAG retrieves relevant information from external sources and provides it to the LLM during response generation.

***

### RAG Architecture

```
User Query
     │
     ▼
Retriever
     │
     ▼
Knowledge Base
(Vector DB, APIs, Documents)
     │
     ▼
Relevant Documents Retrieved
     │
     ▼
LLM Receives Context
     │
     ▼
Generated Response
```

### How RAG Works

#### Step 1: Store Documents

Documents are stored in:

* Vector databases
* APIs
* Document repositories
* Internal knowledge bases

#### Step 2: Retrieve Relevant Information

The system performs similarity search to find relevant documents.

#### Step 3: Provide Context to LLM

Retrieved content is passed to the model.

#### Step 4: Generate Response

The LLM generates an answer using the retrieved context.

### Advantages

#### Up-to-Date Information

Knowledge can be updated without retraining the model.

#### No Training Required

Uses the base LLM as-is.

#### Cost Effective

Avoids expensive fine-tuning processes.

#### High Accuracy

Provides context-specific responses.

#### Supports Private Data

Can securely use internal company information.

### Limitations

#### Infrastructure Required

Needs:

* Vector database
* Retrieval system
* Embedding model

#### Retrieval Quality Matters

Poor document retrieval leads to poor answers.

#### Context Window Limitations

Only a limited amount of retrieved content can be sent to the LLM.

### Best Use Cases

* Customer support systems
* Enterprise knowledge assistants
* FAQ bots
* Document search systems
* Real-time information systems
* Internal company chatbots

#### Ideal When

* Information changes frequently.
* Real-time updates are required.
* Large document repositories exist.

## Comparison Table

| Feature                    | Prompt Engineering | Fine-Tuning | RAG    |
| -------------------------- | ------------------ | ----------- | ------ |
| Requires Training          | No                 | Yes         | No     |
| Cost                       | Low                | High        | Medium |
| Implementation Speed       | Fast               | Slow        | Medium |
| Uses External Data         | No                 | No          | Yes    |
| Supports Real-Time Updates | No                 | No          | Yes    |
| Accuracy for Domain Tasks  | Low-Medium         | High        | High   |
| Infrastructure Requirement | Low                | High        | Medium |
| Expertise Required         | Low                | High        | Medium |
| Best for Company Data      | No                 | Yes         | Yes    |

## When Should You Choose Which?

#### Choose Prompt Engineering When:

* Building prototypes.
* Creating generic AI applications.
* Experimenting quickly.
* Budget is limited.

#### Choose Fine-Tuning When:

* You need specialized behavior.
* Consistency is critical.
* High accuracy is required.
* Domain-specific expertise is needed.

#### Choose RAG When:

* Information changes frequently.
* Real-time data access is required.
* Company documents must be used.
* Cost-effective customization is desired.

## Conclusion

Prompt Engineering, Fine-Tuning, and RAG serve different purposes:

* **Prompt Engineering** customizes responses through instructions without changing the model.
* **Fine-Tuning** teaches the model new domain-specific behavior by retraining it.
* **RAG** enhances responses by retrieving relevant information from external knowledge sources.