# The GCN Link Prediction Model

## 1. GCN as an Encoder: Learning Node Embeddings

The GCN acts as an encoder that takes the graph’s structure and node features and transforms every node into a meaningful vector representation (embedding).

It learns from:

- **Node features**: `x`
- **Graph structure**: `edge_index`

The GCN produces embeddings `z` such that:

- Nodes that _should_ be connected end up **closer** in embedding space
- Nodes that should _not_ be connected become **farther apart**

Example embedding after training:

```
z[node] = [0.12, -0.56, 1.87, ...]
```

In simple terms, the GCN is learning to **understand the graph’s structure and patterns**.

---

## 2. Dot-Product Decoder: Predicting Links

Once node embeddings are learned, link prediction becomes simple:

**Do two nodes point in the same direction in embedding space?**

We compute a score using the dot product:

```
score = z[A] • z[B]
```

Interpretation:

- **Higher score** → nodes likely have an edge
- **Lower score** → nodes are unlikely to connect

This approach mirrors classic graph embedding methods such as **DeepWalk** and **node2vec**.

---

## 3. Training: Teaching the Model to Predict Links

`RandomLinkSplit` prepares:

- **Positive edges** (true edges from the graph)
- **Negative edges** (non-existing edges the model must reject)

The loss function trains the model to:

- Assign **high scores** to positive edges
- Assign **low scores** to negative edges

A fun way to think about it:

> The model works like Tinder for nodes.  
> It learns who should “match” and who shouldn’t.

---

## 4. What the Model Learns

By the end of training, the GCN captures:

### Structural patterns

- Nodes with similar neighbors tend to connect
- Example: In the Cora dataset, papers citing similar papers often cite each other

### Feature similarities

- GCN aggregates feature information over neighbors
- Nodes with similar content get closer in embedding space
- Missing edges can be inferred even without direct connections

### Graph semantics

The model uncovers the **hidden rules** behind how the graph was formed.

---

## 5. Evaluation

The model is evaluated using:

- Validation edges
- Test edges

Key metrics:

- **AUC (Area Under ROC Curve)**  
  Measures how well positive edges are ranked above negative ones

- **AP (Average Precision)**  
  Focuses on quality of positive predictions

Typical good performance: **AUC ≥ 0.90**  
This means the model has effectively captured the underlying graph structure.

---
