# Image Similarity Recommendation System

---

## Overview

This project implements a **Visual Content-Based Recommendation System** that suggests similar products based on their physical appearance (color, shape, texture), rather than on textual metadata (price, brand, model).

The system uses **Deep Learning** to "see" and encode product images into numerical vectors. This allows it to find visual matches within a catalog, acting as a powerful recommendation engine for e-commerce or fashion. The project was developed as a demonstration of Transfer Learning techniques and similarity search.

---

## How It Works

The recommendation process is divided into three main stages:

1.  **Feature Extraction (Embeddings):** An image is processed by a pre-trained **Convolutional Neural Network (CNN)**, specifically **ResNet50**. The network's final classification layer is removed, and the output is a **2048-dimensional numerical vector** (the *embedding*), which serves as the image's visual "fingerprint."
2.  **Catalog Vectorization:** All products in the catalog are processed to generate and store their respective *embeddings*.
3.  **Similarity Search (KNN):** When querying a product, the system calculates the **Cosine Distance** between the query product's embedding and all catalog embeddings. The **K-Nearest Neighbors (KNN)** algorithm identifies the closest vectors (lowest distance), which are returned as the most visually similar recommendations.

---

## Prerequisites and Execution

### 1. Prerequisites

* **Google Account:** Necessary to use Google Colab.
* **Dataset:** The `Colors_Products.zip` file must be uploaded to your Google Drive.

### 2. Execution (Google Colab)

The project is executed entirely within a Google Colab notebook:

1.  **Mount Drive:** Run the first cell to connect Colab to your Google Drive and access the zipped file.
2.  **Adjust Path:** Set the `zip_path` variable to the exact location of your file on Drive.
3.  **Run the Parts:** Follow the notebook's order, executing the cells for each part sequentially:
    * **Part 1:** Data Preparation (Unzipping and DataFrame Creation).
    * **Part 2:** Model Definition (ResNet50 Extractor).
    * **Part 3:** Embeddings Extraction.
    * **Part 4:** Recommendation System (KNN).
    * **Part 5:** Results Visualization.

---

## Technologies Used

| Category | Technology | Project Role |
| :--- | :--- | :--- |
| **Main Environment** | **Google Colab** | Development platform for easy access to GPU/TPU resources. |
| **Deep Learning** | **TensorFlow / Keras** | Used to create the CNN model for visual feature extraction. |
| **Base Model** | **ResNet50** | Used for **Transfer Learning**, extracting robust visual features pre-trained on ImageNet. |
| **Similarity** | Scikit-learn (`NearestNeighbors`) | Implementation of the **K-Nearest Neighbors (KNN)** algorithm with **Cosine Distance**. |
| **Data and Utilities** | Pandas, NumPy, Matplotlib | Structuring the product catalog, handling embedding vectors, and visualizing results. |
