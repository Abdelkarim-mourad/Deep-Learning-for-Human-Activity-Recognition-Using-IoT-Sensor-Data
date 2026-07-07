# Deep Learning for Human Activity Recognition Using IoT Sensor Data

## Project Overview

This project applies deep learning to Human Activity Recognition using IoT sensor data. The objective is to classify human activities based on smartphone inertial sensor signals, including accelerometer and gyroscope readings.

The project uses the UCI Human Activity Recognition dataset and implements a 1D Convolutional Neural Network to classify time-series sensor data into different activity categories.

## Dataset

The dataset used is the UCI HAR Using Smartphones dataset.

It contains sensor data collected from smartphones worn by participants while performing daily activities. The data includes accelerometer and gyroscope signals sampled at 50 Hz.

### Activities Classified

The model classifies six activities:

- WALKING
- WALKING_UPSTAIRS
- WALKING_DOWNSTAIRS
- SITTING
- STANDING
- LAYING

### Dataset Details

- Number of subjects: 30
- Sensor type: Smartphone accelerometer and gyroscope
- Sampling rate: 50 Hz
- Window size: 2.56 seconds
- Number of channels: 9
- Training samples: 7,352
- Testing samples: 2,947

## Methodology

The project follows a complete deep-learning workflow:

1. Load the UCI HAR dataset
2. Check for missing values
3. Split the training data into training and validation sets
4. Standardize each sensor channel
5. Build a 1D Convolutional Neural Network
6. Train the model using Adam optimizer
7. Evaluate the model using accuracy, precision, recall, F1-score, confusion matrix, and ROC curves

## Model Architecture

The model is based on a 1D Convolutional Neural Network.

The architecture includes:

- Conv1D layers
- Batch Normalization
- MaxPooling
- Dropout
- Global Average Pooling
- Dense classification layers
- Softmax output layer

The model contains approximately 232,000 parameters.

## Training Configuration

- Optimizer: Adam
- Loss function: Sparse Categorical Crossentropy
- Batch size: 64
- Maximum epochs: 40
- Early stopping was used to prevent overfitting
- Learning rate reduction was used when validation loss stopped improving

## Results

The model achieved strong results on the test set.

### Aggregate Test Metrics

| Metric | Value |
|---|---:|
| Accuracy | 90.91% |
| Macro Precision | 91.10% |
| Macro Recall | 91.20% |
| Macro F1-score | 91.12% |
| Weighted Precision | 90.97% |
| Weighted F1-score | 90.91% |
| Best Validation Accuracy | 97.28% |

### Per-Class Performance

| Activity | Precision | Recall | F1-score |
|---|---:|---:|---:|
| WALKING | 0.978 | 0.972 | 0.975 |
| WALKING_UPSTAIRS | 0.901 | 0.962 | 0.930 |
| WALKING_DOWNSTAIRS | 0.984 | 0.990 | 0.987 |
| SITTING | 0.772 | 0.786 | 0.779 |
| STANDING | 0.842 | 0.812 | 0.827 |
| LAYING | 0.990 | 0.950 | 0.970 |

## Discussion

The model performs very well on dynamic activities such as walking, walking upstairs, and walking downstairs. It also performs well on the laying activity.

Most classification errors occur between SITTING and STANDING. This is expected because both activities are static and have similar sensor patterns, especially when using a waist-mounted smartphone sensor.

The difference between validation accuracy and test accuracy is mainly due to subject-to-subject variation. The validation set comes from the training subjects, while the test set contains different subjects.

## Conclusion

This project demonstrates that a 1D Convolutional Neural Network can effectively classify human activities using IoT sensor time-series data. The model learns directly from raw accelerometer and gyroscope signals and achieves high accuracy without manual feature engineering.

The system can be adapted to other wearable IoT or smart-device sensor datasets for activity recognition and time-series classification tasks.
