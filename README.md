# 🛠️ CadQuery Code Generation Baseline

This repository provides a baseline model for generating CadQuery code from 3D model images using image retrieval based on CLIP embeddings.

## 📄 Description

- **Dataset**: [CADCODER/GenCAD-Code](https://huggingface.co/datasets/CADCODER/GenCAD-Code) — 147,000 pairs of rendered 3D images and corresponding CadQuery code.
- **Baseline Approach**:
  - Extract image embeddings using [`openai/clip-vit-base-patch32`](https://huggingface.co/openai/clip-vit-base-patch32).
  - Index embeddings from the training set.
  - For a given query image, retrieve the CadQuery code associated with the most similar training image (based on cosine similarity).
- **Evaluation Metrics**:
  - ✅ **Valid Syntax Rate (VSR)**: Measures whether the generated CadQuery code executes without errors.
  - 📐 **Best IOU**: Measures geometric similarity between 3D meshes produced by the retrieved vs. ground-truth code.

---

## 📦 Installation
pip install transformers datasets torch torchvision torchaudio tqdm pillow cadquery trimesh scipy



## Next Steps
This baseline uses retrieval only. For better performance:

🔧 Fine-tuning the CLIP model on this specific dataset to better capture domain-specific features.

🧠 Using a generative model to directly produce CadQuery code from images (e.g. vision-to-code transformers).

⚡ Implementing a faster and more scalable retrieval system, such as FAISS.

✅ Adding advanced post-validation or correction mechanisms to filter or fix invalid generated code.


