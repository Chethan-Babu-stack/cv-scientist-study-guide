# Important Machine Learning Terminologies with Explanation

## 1. Self-attention

### **Definition:**
Self-attention allows a sequence to attend to itself. That means each element (e.g., word or image patch) looks at all other elements in the same sequence to gather context.

### **Use Case:**
Used in unimodal settings — e.g., in language models, vision transformers, etc.

### **Mechanism**
Each input vector is transformed into:
- **Query (Q)**
- **Key (K)**
- **Value (V)**

For each token:
```text
attention_scores = softmax(Q @ Kᵀ / sqrt(d_k))
output = attention_scores @ V
```
### **Benefits**
- Captures contextual relationships (e.g., syntax, semantics).

- Enables dynamic weighting of information in the sequence.

## 2. Cross-attention
### **Definition:**
Cross-attention allows one sequence (say, queries) to attend to a different sequence (the context, which provides keys and values).

### **Use Case:**
Used in multimodal or encoder-decoder settings.

### **Examples:**

- In Transformer decoder (e.g., machine translation): The decoder attends to encoder outputs.

- In vision-language models: Text queries attend to image embeddings.

```text
Q = from decoder or target sequence
K, V = from encoder or source sequence
attention_score = softmax(Q @ Kᵀ / sqrt(d_k))
output = attention_score @ V
```

### **Benefits**
- Inject external context into a target sequence

- Align different modalities (e.g., text tokens attending to image regions)