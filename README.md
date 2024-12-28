LINK TO MOVIES DATABASE: https://drive.google.com/file/d/1X2WAngDM85mX1tfxqh4Nv1wfyZbzfWfM/view?usp=sharing

# Comparing Sentence Embedding Models and Dimensionality Reduction for Movie Plot Similarity

## Overview

This project compares the performance of two sentence embedding models, **all-mpnet-base-v2** and **multi-qa-mpnet-base-dot-v1**, for analyzing movie plot similarities. The study also explores the effectiveness of TF-IDF-based dimensionality reduction with SVD in identifying relevant movie plots based on specific queries.

---

## Sentence Embedding Models

### Models Selected
1. **all-mpnet-base-v2**: Best for general quality.
   - Max Sentence Length: 384
   - Embedding Size: 768
2. **multi-qa-mpnet-base-dot-v1**: Optimized for diverse (question, answer) pairs.
   - Max Sentence Length: 512
   - Embedding Size: 768

### Preprocessing
- Movie plots were truncated to fit each model's maximum sentence length.
- Embeddings were generated for a subset of plots to calculate truncation ratios.

---

## Cosine Similarity Analysis

### Results
- Similarity scores were computed for the first 5 movie plots.
- **Model 1 (all-mpnet-base-v2):**
  - Similarity range: 0.24 to 0.65
- **Model 2 (multi-qa-mpnet-base-dot-v1):**
  - Similarity range: 0.28 to 0.69 (higher scores than Model 1)

### Observations
- Despite better similarity scores, **Model 1** achieved higher precision values for specific queries, suggesting its relevance to direct query terms like "pirate."

---

## TF-IDF and SVD Dimensionality Reduction

### Steps
1. **TF-IDF Matrix Creation:**
   - Top 5,000 terms selected.
   - Sparse matrix converted to dense format for interpretability.
2. **Dimensionality Reduction:**
   - Applied SVD with 200 and 500 components.

### Query Analysis
- Three predefined queries: 
  - "Inspiring Pirate Adventure"
  - "Depressing Ghost Story"
  - "Based on a True Story"
- Cosine and dot product similarities computed between query embeddings and movie plots.

### Precision Results
| Query                        | Cosine (200) | Dot (200) | Cosine (500) | Dot (500) |
|------------------------------|--------------|-----------|--------------|-----------|
| Inspiring Pirate Adventure   | 3/3, 4/5, 5/7 | 3/3, 4/5, 5/7 | 3/3, 4/5, 5/7 | 3/3, 4/5, 5/7 |
| Depressing Ghost Story       | 3/3, 5/5, 6/7 | 3/3, 5/5, 6/7 | 3/3, 5/5, 6/7 | 3/3, 5/5, 6/7 |
| Based on a True Story        | 2/3, 3/5, 5/7 | 1/3, 1/5, 1/7 | 1/3, 1/5, 1/7 | 1/3, 1/5, 1/7 |

---

## Comparative Observations

1. **Embedding Models:**
   - **multi-qa-mpnet-base-dot-v1** delivered higher similarity scores but weaker precision.
   - **all-mpnet-base-v2** exhibited lower similarity but stronger alignment with specific queries.

2. **Dimensionality Reduction:**
   - SVD improved interpretability and relevance.
   - Results were more consistent with direct queries, outperforming embedding models in precision.

3. **TF-IDF Approach:**
   - Consistently identified relevant movies for "pirate" and "ghost" queries.
   - Struggled with the "true story" query due to broader contextual themes.

---

## Conclusion

- **Dimensionality Reduction vs. Sentence Embeddings:** Dimensionality reduction methods, specifically SVD on TF-IDF matrices, demonstrated superior precision and relevance to specific queries compared to sentence embedding models.
- **Embedding Model Choice:** While **multi-qa-mpnet-base-dot-v1** excels at general similarity, **all-mpnet-base-v2** is better suited for queries demanding specificity.
- Future improvements could involve dataset refinement to eliminate redundancy (e.g., multiple versions of "Treasure Island").

---

## Code and Results

The full implementation and detailed outputs are documented in the accompanying notebooks `Proj.ipynb` and `Cluster.ipynb`.

---

## Questions?

Feel free to reach out for additional clarifications or collaboration opportunities.
