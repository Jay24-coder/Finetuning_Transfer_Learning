# Car vs Plane Classifier Using Transfer Learning (VGG16)

This project demonstrates a binary image classification task using **Transfer Learning** with the **VGG16** architecture from Keras. The model is trained to distinguish between images of **cars** and **planes**.

---

## 📁 Project Structure

```
├── Cars/ # Folder containing car images (.jpg)
├── Planes/ # Folder containing plane images (.jpg)
├── imagenet_class_index.json
├── car_plane_classifier.py # Your Python script
└── README.md
```

---

## 📌 Features

- Uses **VGG16** pretrained on **ImageNet**.
- Freezes all convolutional layers and adds a new classifier head.
- Loads car and plane images from separate folders.
- Applies **preprocess_input** from VGG16 for consistent preprocessing.
- Binary classification using a sigmoid output unit.

---

## 🧠 Model Architecture

- Pretrained VGG16 (all layers frozen)
- Added final `Dense(1, activation='sigmoid')` layer for binary classification
- Compiled with `adam` optimizer and `binary_crossentropy` loss

---

## 🖼️ Dataset

- Two categories:
  - `Cars/` – Labeled as `0`
  - `Planes/` – Labeled as `1`

Ensure the folders `Cars/` and `Planes/` contain `.jpg` images for training.

---

## 🧪 Training

```python
model_for_cars_planes.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])
model_for_cars_planes.fit(x=x, y=y, epochs=5, validation_split=0.2)
```
- Images are resized to 224x224.
- Training uses 80% of the data, 20% is used for validation.
- The VGG16 layers are not trainable (frozen), only the new classifier layer is trained.

## 🛠️ How to Run
1. Install dependencies:

```
pip install tensorflow pandas numpy
```
2. Place your images inside Cars/ and Planes/ directories.
3. Ensure you have the imagenet_class_index.json file in the same directory (for class name mapping, though not directly used in training).

## 📌 Notes
- This is a basic example of transfer learning for binary classification.
- You can further improve performance by:
    - Unfreezing and fine-tuning top layers of VGG16
    - Adding dropout or batch normalization
    - Using data augmentation