# Vibe-Matcher-Submission
a mini rec system for fashion data: Input vibe query → Embed products → Match top-3 via cosine similarity.




# 🎧 Vibe Matcher — AI-Powered Fashion Recommendation Prototype

## 🧠 Introduction
The **Vibe Matcher** is a mini recommendation system prototype that connects *fashion items* to *user vibes*. The goal is to allow users to input a mood or aesthetic (like “energetic urban chic”) and get the top-3 matching products based on semantic similarity.  

This project demonstrates how AI and embeddings can be used to create intelligent, vibe-based fashion discovery experiences.

---

## 🚀 Project Overview

### 🏗️ Workflow
1. **Data Preparation**  
   Created a dataset of 20 fashion items with their descriptions and vibe tags such as *boho, street, elegant, sporty,* etc., stored in a Pandas DataFrame.

2. **Text Embedding Generation**  
   Originally, the plan was to use OpenAI’s `text-embedding-ada-002` model.  
   However, after hitting the **free-tier limit**, I switched to using **SentenceTransformer** (`all-MiniLM-L6-v2`) from Hugging Face.  

   **Why SentenceTransformer?**
   - It’s free, efficient, and can run locally.
   - Produces high-quality sentence embeddings.
   - Widely used for semantic search and recommendation systems.

3. **Similarity Computation**  
   - Encoded all product descriptions and user query.
   - Used **cosine similarity** (`sklearn.metrics.pairwise.cosine_similarity`) to find the top-3 closest matches.

4. **Evaluation & Testing**  
   - Tested 3 sample queries:  
     e.g., “energetic urban chic”, “soft romantic date night”, “minimal academic winter style”.  
   - Logged similarity scores and query latency using `timeit`.

5. **Results Visualization**  
   - Displayed top-3 ranked products with their names, vibe tags, and similarity scores.
   - Counted matches above threshold (similarity > 0.7) as “good”.

---

## 🧰 Tech Stack
- **Python 3.10+**
- **Pandas** — dataset handling  
- **SentenceTransformers** — text embeddings (`all-MiniLM-L6-v2`)  
- **scikit-learn** — cosine similarity  
- **Matplotlib** — latency visualization  
- **Timeit** — performance measurement  

---

## 🧩 Sample Output

**Query:** “Energetic urban chic”  

| Rank | Product | Similarity | Vibes |
|------|----------|-------------|--------|
| 1 | Urban Edge Jacket | 0.89 | [urban, edgy, night] |
| 2 | Neon Puffer Jacket | 0.84 | [street, bright, sporty] |
| 3 | Futuristic Runner Shoes | 0.80 | [tech, futuristic, sport] |

---

## 📊 Evaluation Metrics

| Metric | Description |
|--------|--------------|
| Cosine Similarity > 0.7 | Counted as a "good" match |
| Latency per query | Measured in milliseconds |
| Recall@3 | Fraction of relevant products in top-3 |

---

## 💭 Reflection

### ✅ Improvements & Future Work
1. **Pinecone / FAISS Integration:**  
   For scalability and real-time vector search, embeddings can be indexed in Pinecone or FAISS for millisecond retrieval.

2. **Multimodal Expansion:**  
   Include **image embeddings** (CLIP) to match vibes visually along with text.

---

### ⚙️ Edge Cases Handled
- Fallback message when no similarity > 0.6 (“No perfect vibe found — want to try a different mood?”).  
- Handled empty or irrelevant queries gracefully.  
- Normalized embeddings to ensure fair cosine comparison.  

---

## 🏁 Conclusion
The **Vibe Matcher** showcases how lightweight AI models can power creative, emotion-driven recommendation systems. Even with local embeddings, the model provides fast, relevant, and scalable results — making it a promising foundation for next-gen AI personalization.

