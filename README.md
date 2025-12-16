# CLIP Zero-Shot Harmful Content Analysis

This project performs **zero-shot harmful content analysis** on images using **OpenAI's CLIP model (ViT-B/32)**.  

The system measures the **semantic similarity between images and predefined text labels** to estimate potential harm, without any training or hard class labels.

---

## 🔍 Method

1. **Images & Text Labels**  
   - Images are loaded from the `images/` folder.  
   - Example text labels: `"weapon"`, `"violence"`, `"injury"`, `"sport equipment"`, `"household item"`  

2. **Embedding & Similarity Computation**  
   - Image and text features (embeddings) are extracted using CLIP.  
   - Features are normalized and **cosine similarity** is calculated to evaluate image–text relationships.  

3. **Heatmap Visualization**  
   - A similarity matrix is visualized using a **heatmap**.  
   - Each cell shows the similarity score between an image and a text label.  

4. **Predicted Matches**  
   - The text label with the highest similarity is selected for each image.  
   - Images are displayed with their predicted label and similarity score.  

5. **Harmful / Safe Decision**  
   - Text labels are grouped as **risk-like** (`weapon`, `violence`, `injury`) or **safe-like** (`sport equipment`, `household item`).  
   - For each image, the average similarity with risk and safe labels is computed.  
   - Margin = risk score − safe score  
     - `margin > 0` → **POTENTIALLY HARMFUL**  
     - `margin ≤ 0` → **LIKELY SAFE**  

---

## ⚡ Features

- **Zero-shot:** No training required; uses pre-trained CLIP model.  
- **Context-aware:** Semantic similarity between images and text guides the risk evaluation.  
- **Visualization:** Heatmaps and matplotlib plots display image–text relationships.  
- **Flexible:** Easily add new images or text labels.

---

## 📌 Usage

1. Place images in the `images/` folder.  
2. Define your text labels in the `text_labels` list.  
3. Run the code to:  
   - Visualize the similarity heatmap  
   - See predicted image–text matches  
   - Obtain harmful/safe analysis
