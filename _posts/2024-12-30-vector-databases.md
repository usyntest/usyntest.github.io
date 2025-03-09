---
layout: post
title: Introduction to Vector Databases
date: 2024-12-24 16:40:16
description: Modern applications require more than just exact search—they need similarity search, and vector databases enable this at scale.
tags: search, vector-database, ai
categories: database
pretty_table: true
---

## Introduction

Traditional databases are great at storing and retrieving structured data—user records, transactions, logs—where exact matching works well. But what if you want to search for similar things instead of exact matches?

Think of searching for an image of a golden retriever. A traditional database would need exact metadata tags like `"dog"` or `"golden retriever"` to match it. But what if you only had the image itself? This is where vector databases come in.

Vector databases store high-dimensional embeddings, numerical representations of unstructured data like text, images, and audio. Instead of keyword-based searches, they use Approximate Nearest Neighbor (ANN) search to find similar vectors based on distance metrics like cosine similarity or Euclidean distance.

With the rise of AI and machine learning, applications like semantic search, recommendation systems, anomaly detection, and AI chatbots rely heavily on vector search. While some traditional databases offer vector search extensions (e.g., PostgreSQL’s pgvector), dedicated vector databases like Milvus, Qdrant, Weaviate, and Pinecone are built specifically for high-speed, large-scale similarity search.

In this blog, I’ll break down:

1. What vector databases are and how they work?
2. How they differ from SQL and NoSQL databases?  
3. Why they are essential for modern AI-driven applications?
4. The key indexing techniques behind vector search
5. How to get started with vector databases?  

---
## What are Vector Databases?

Vector databases are specialized databases designed to store and retrieve high-dimensional vector embeddings efficiently. Unlike traditional databases that rely on exact matching, vector databases perform similarity search by comparing numerical representations of data points.

##### Key Concept: Storing and Searching Embeddings
Machine learning models can convert unstructured data—text, images, audio—into vector embeddings, which are numerical arrays that capture the meaning and relationships within the data. These embeddings are stored in a vector database, allowing for Approximate Nearest Neighbor (ANN) search to quickly find similar items.

For example:

- A text embedding might represent the meaning of a sentence, enabling semantic search (e.g., `"cheap laptop"` matching `"affordable notebook"`).
- An image embedding might encode visual features, enabling image similarity search (e.g., retrieving dog photos similar to a given one).

Instead of retrieving exact matches, vector databases return results ranked by how similar they are to the query, based on distance metrics like cosine similarity, Euclidean distance, or dot product.

---
## How Vector Search Works

Vector search operates on the principle of **finding the closest vectors in high-dimensional space**. Since storing and searching millions (or billions) of vectors is computationally expensive, efficient algorithms like Approximate Nearest Neighbor (ANN) search are used instead of brute-force comparisons.

##### Distance Metrics for Similarity Search

To determine how "close" or "similar" two vectors are, vector databases use distance functions such as:

###### 1. Euclidean Distance (L2 norm)
Measures the straight-line distance between two points in space. Best for numeric data and structured patterns.  

$$ d(x, y) = \sqrt{\sum (x_i - y_i)^2} $$

###### 2. Cosine Similarity
Measures the angle between two vectors, focusing on direction rather than magnitude. Often used for **text embeddings**.   

$$ \text{similarity} = \frac{x \cdot y}{\|x\| \|y\|} $$

###### 3. Dot Product Similarity
A variation of cosine similarity, often used in recommendation systems where larger values indicate stronger similarity.  

$$ \text{similarity} = x \cdot y $$

Depending on the use case (text search, image retrieval, recommendation systems), different databases and models optimize for specific distance metrics.

---
## Indexing Techniques in Vector Databases

Since performing a brute-force search across millions of vectors is too slow, vector databases use indexing techniques to speed up search by organizing and clustering vectors efficiently. Here are some of the most common indexing methods:

###### 1. HNSW (Hierarchical Navigable Small World)
- A graph-based approach that builds a multi-layered network of vectors.
- Uses greedy search to quickly navigate through connected nodes to find the nearest neighbors.
- Provides fast and accurate searches, widely used in Qdrant, FAISS, and Milvus.

###### 2. IVF (Inverted File Index)
- Clusters vectors into Voronoi cells and searches only within the relevant cluster.
- Instead of scanning all vectors, it narrows down search space, making it memory efficient.
- Used in FAISS and Milvus for large-scale vector retrieval.

###### 3. PQ (Product Quantization)
- Compresses high-dimensional vectors into smaller representations using quantization techniques.
- Useful when dealing with limited memory resources, as it reduces the storage size of vectors.
- Works well in combination with IVF for scalable vector search.


##### Choosing the Right Indexing Method

| Method | Best For | Pros | Cons |
|--------|---------|------|------|
| HNSW  | High-accuracy search | Fast & scalable | High memory usage |
| IVF   | Large-scale retrieval | Memory-efficient | Lower recall for small datasets |
| PQ    | Memory optimization | Reduces storage size | Slight drop in accuracy |

> **Note:** Each indexing method balances speed, memory efficiency, and accuracy. The right choice depends on the dataset size, query speed requirements, and available resources.

---
## Use Cases of Vector Databases

Vector databases power many AI-driven applications where **similarity search** is crucial. Instead of relying on exact keyword matches, these databases allow systems to find **semantically similar** results, making them essential for:  

###### 1. Semantic Search
Traditional keyword-based search systems struggle with synonyms and contextual meaning. Vector databases enable **semantic search**, where search queries are matched based on their meaning rather than exact words.  

**Example:** Searching for `"affordable phone"` returns `"cheap smartphone deals"` even though the words are different.  

###### 2. Image & Video Search
Vector embeddings allow **reverse image search**, where users can upload an image to find visually similar ones.  

**Example:** Google Lens and Pinterest use vector embeddings to match images with similar content.  

###### 3. Personalized Recommendations
Recommendation systems use vector embeddings to suggest **similar items** based on user preferences.  

**Example:**  
- **E-commerce:** `"Users who liked this product also liked..."`  
- **Streaming services:** `"Because you watched X, you might like Y"`  

###### 4. Anomaly Detection & Fraud Prevention
Vector search helps detect anomalies by identifying outliers in high-dimensional data.  

**Example:**  
- **Finance:** Detecting fraudulent transactions by spotting unusual spending patterns.  
- **Cybersecurity:** Identifying unusual login behavior in a system.  

###### 5. AI Chatbots & RAG (Retrieval-Augmented Generation)
Vector databases improve AI chatbots by enabling **context-aware responses** through similarity search.  

**Example:** ChatGPT-like assistants use vector search to retrieve relevant documents for better answers.  

## Challenges & Limitations  

While vector databases are powerful, they come with trade-offs:  

###### 1. Memory Usage 
- Graph-based indexing (HNSW) can be **memory-intensive**, requiring large RAM for high recall.  
- PQ and IVF reduce memory usage but may sacrifice accuracy.  

###### 2. Indexing Speed vs. Query Speed  
- **HNSW:** Fast queries but slow indexing.  
- **IVF:** Faster indexing but slightly slower queries.  
- **PQ:** Best for reducing memory but adds latency to queries.  

###### 3. Precision vs. Recall
- Approximate nearest neighbor (ANN) methods **prioritize speed over perfect accuracy**.  
- Fine-tuning parameters like **ef_construction (HNSW) or nprobe (IVF)** is required to balance speed and accuracy.  

---

## Getting Started with a Vector Database (Qdrant Example)  

Let’s set up **Qdrant**, an open-source vector database, and run a **basic similarity search**.  

###### 1. Install Qdrant Server
Run Qdrant locally using Docker:  
```bash
docker run -p 6333:6333 qdrant/qdrant
```  

###### 2. Install Qdrant Client  
```bash
pip install qdrant-client numpy
```  

###### 3. Create a Collection & Insert Vectors
```python
import numpy as np
from qdrant_client import QdrantClient
from qdrant_client.models import PointStruct

# Connect to Qdrant server
client = QdrantClient("localhost", port=6333)

# Create a collection
client.recreate_collection(collection_name="my_vectors", vector_size=3, distance="Cosine")

# Insert some vectors
vectors = [
    PointStruct(id=1, vector=[0.1, 0.2, 0.3]),
    PointStruct(id=2, vector=[0.4, 0.5, 0.6]),
    PointStruct(id=3, vector=[0.7, 0.8, 0.9]),
]
client.upsert(collection_name="my_vectors", points=vectors)
```  

###### 4. Perform a Similarity Search  
```python
query_vector = [0.15, 0.25, 0.35]

results = client.search(
    collection_name="my_vectors",
    query_vector=query_vector,
    limit=2  # Return top 2 similar vectors
)

print(results)
```  

This will return the **most similar vectors** based on cosine similarity! 🎯  

---
## Conclusion

Vector databases are transforming AI-driven applications by enabling fast, scalable similarity search for text, images, audio, and more. As models get larger and embeddings become a core part of AI workflows, vector search will be a crucial component of modern data infrastructure.

##### Future Trends 🚀  
  
✅ Hybrid Search – Combining vector and keyword search for better retrieval.  
✅ Efficient Indexing – Reducing memory usage with better compression.  
✅ Cloud-native Vector Databases – Fully managed solutions like Pinecone.  
✅ RAG-powered AI Agents – Better AI models using retrieval-augmented generation.  

With the rise of LLMs and AI-powered search, vector databases will only become more important in the future. If you haven’t explored them yet, now’s the perfect time to start! 🚀
