#  Multi-Stage CNN Classification Project  

This project focuses on building a **multi-stage Convolutional Neural Network (CNN) system** for visual classification of fashion items such as clothing and footwear.  
Each model is trained separately for a specific subtask, forming a hierarchical pipeline that progressively refines classification accuracy.  

---

## Dataset Overview

The dataset is provided as a compressed ZIP file. To use the data, follow these steps:

1. **Download the ZIP file** containing the dataset from the link below:
   - [https://drive.google.com/file/d/1Eldk4vFkP5yoY-pCkfZzOMB-xECIeh3p/view?usp=drive_link]

2. **Extract the ZIP file** to obtain the full dataset folder.

3. Place the extracted folder in the root directory of this project, so it appears as `Dataset/`.

4. The dataset folder contains multiple subfolders, each with `.npz` files for **training**, **validation**, and **testing**.


---

##  Model Overview  

###  Primary Category Model  
Classifies images into **three main groups**:  
Glasses/Sunglasses, Trousers/Jeans , and Shoes .  
- Built using a simple CNN with two convolutional layers and one dense layer.  
- Compiled with **Adam optimizer** and **Sparse Categorical Crossentropy** loss.  
- Includes **EarlyStopping** and **TensorBoard** callbacks for training stability.

---

###  Pants Classification Model  
Classifies pants images into **four categories**:  
Trousers Male , Jeans Male , Trousers Female , and Jeans Female .  
- Includes **L2 regularization** on all layers to prevent overfitting.  
- Utilizes **data augmentation** (rotation, shift, zoom, horizontal flip).  
- Compiled with **Adam optimizer** and **Sparse Categorical Crossentropy** loss.  

---

###  Eyewear Classification Model  
Classifies eyewear images into **two categories**:  
Glasses  and Sunglasses .  
- Lightweight CNN with two convolutional layers and one dense layer.  
- Trained for 15 epochs with early stopping and validation monitoring.

---


###  Footwear Classification System (Three-Stage)  

#### Stage 1 – Gender Classification  
Predicts whether a shoe belongs to **Male** or **Female**.  
Output of this model determines which classifier (male or female) will be used next.

#### Stage 2 – Male Footwear Model  
Classifies male shoes into **five categories**:  
Boots, Trainers/Sneakers, Sandals/Slippers, Formal shoes, and Others.

#### Stage 3 – Female Footwear Model  
Classifies male shoes into **six categories**:  
Boots, Ballerina Shoes, Trainers/Sneakers, Sandals/Slippers, Formal shoes, and Others.

All three shoe models share a similar CNN architecture with two convolutional layers, one fully connected layer (1024 neurons), and an output layer.  
Each model uses **EarlyStopping** and **TensorBoard** callbacks for optimized training.

---

##  Training Configuration  

- **Epochs:** 15–20  
- **Batch size:** 64  
- **Optimizer:** Adam  
- **Loss:** SparseCategoricalCrossentropy  
- **Callbacks:** EarlyStopping, TensorBoard  
- **Augmentation:** rotation, zoom, shift, horizontal flip  

---

##  Results(accuracy)  

Primary: 99%

Eyewear: 95%

Pants: 65%

Shoes(Gender): 76%    Shoes(Male): 89%     Shoes(Female): 82%
---

##  Evaluation & Visualization  

Each model’s performance is analyzed using:
- **Confusion Matrix** to visualize class-wise predictions  
- **Classification Report** for precision, recall, and F1-score  
- **TensorBoard Logs** to monitor loss and accuracy trends  

---


