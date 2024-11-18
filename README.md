## **Cat vs Dog Classification**
This notebook is based on the course **INFO6105 @ NEU**.  
[Link to Colab Notebook](https://colab.research.google.com/drive/14qpofloJSwikBrTSJFBoxtkh-WL0-HIV?usp=sharing)

---

### **Key Objectives**
1. **Understand the Cat vs Dog Dataset**: A binary classification task involving color images with three channels (RGB).
2. Perform experiments to optimize model performance by tuning architecture and hyperparameters.

---

### **Steps and Attempts**
#### **1. Data Preprocessing**
- **Objective**: Resize images to ensure uniformity in input dimensions.
- **Details**: Resized images from their original dimensions to 64x64 initially.
- **Reason**: Ensures compatibility with the model input layer and reduces computational requirements.

---

#### **2. Dropout Regularization**
- Introduced **dropout layers** to prevent overfitting.
- **How It Works**: Randomly sets a fraction of input units to zero during training.
- **Why It's Useful**: 
  - Reduces co-dependency among neurons.
  - Improves generalization performance on unseen data.

---

#### **3. Metric Selection**
- Opted to monitor **accuracy** over **loss** for early stopping.
- **Why**: Loss proved too sensitive in this case, leading to premature stopping. Accuracy provided a more stable indicator of model improvement.

---

#### **4. Early Stopping Callback**
- Added an **early stopping** mechanism based on validation accuracy.
- **How It Works**: Stops training if the validation accuracy does not improve for a defined number of epochs.
- **Benefits**:
  - Saves computational resources.
  - Prevents unnecessary overfitting during prolonged training.

---

### **Batch Size and Model Architecture**
#### **Batch Size Comparison**
- **Objective**: Determine the impact of batch sizes ranging from 8 to 512.
- **Usually**:
  - Smaller batches: Introduced gradient noise, helping escape local minima but requiring more updates.
  - Larger batches: Faster optimization steps but showed signs of overfitting.

- **But!From the result images below, patterns are not very clear**

<img src="https://github.com/zysea23/Markdown_Images/blob/main/A&L-batch=8_0.72.png?raw=true" alt="batch=8" width="700" height="300">
<img src="https://github.com/zysea23/Markdown_Images/blob/main/A&L-batch=16_0.74.png?raw=true" alt="batch=16" width="700" height="300">
<img src="https://github.com/zysea23/Markdown_Images/blob/main/A&L-batch=32_0.76.png?raw=true" alt="batch=32" width="700" height="300">
<img src="https://github.com/zysea23/Markdown_Images/blob/main/A&L-batch=64_0.766.png?raw=true" alt="batch=64" width="700" height="300">
<img src="https://github.com/zysea23/Markdown_Images/blob/main/A&L-batch=128_0.74.png?raw=true" alt="batch=128" width="700" height="300">
<img src="https://github.com/zysea23/Markdown_Images/blob/main/A&L-batch=256_0.71.png?raw=true" alt="batch=256" width="700" height="300">
<img src="https://github.com/zysea23/Markdown_Images/blob/main/A&L-batch=512_0.75.png?raw=true" alt="batch=512" width="700" height="300">



#### **Model Architecture Experiments**
- Experimented with **resize dimensions** (64x64 vs. 128x128):
  - Larger dimensions improved feature resolution **(not much!)** but increased computation time **(not much in this case too)**.

---

### **Summary**
The experiments in this notebook highlight:
- Increased the number of layers in the network to capture more complex features.
- The importance of preprocessing steps, such as **resizing** and **dropout**, for generalization.
- **Early stopping based on accuracy** provides a more robust criterion than loss in this case.
- Trade-offs in batch sizes and input dimensions must be balanced to achieve optimal performance.
- The final test set accuracy reached approximately 75%, likely reflecting the model's capacity and the limitations of the available training data, as no significant improvement was observed despite extensive parameter tuning.

