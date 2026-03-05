# Airfoil Noise Prediction using Apache Spark

An end-to-end Machine Learning pipeline built with PySpark to predict airfoil self-noise. This repository contains the final project for the **Machine Learning with Apache Spark** course by IBM on Coursera.

## 📝 Project Overview

The goal of this project is to assist an aeronautics consulting company in efficiently designing airfoils for planes and sports cars. Using the **NASA Airfoil Self Noise dataset**, this project demonstrates how to perform data engineering (ETL) and build a robust machine learning pipeline using Apache Spark to predict the sound level (`SoundLevelDecibels`) based on various aerodynamic and acoustic features.

## 🛠️ Technologies Used

- **Apache Spark (PySpark)**
- **Python 3**
- **Machine Learning** (Linear Regression, Feature Scaling, Pipelines)
- **Jupyter Notebook**

## 📊 Dataset

The original dataset is the [NASA Airfoil Self-Noise dataset](https://archive.ics.uci.edu/dataset/291/airfoil+self+noise). It contains different size NACA 0012 airfoils at various wind tunnel speeds and angles of attack.

**Features:**

- `Frequency` (Hz)
- `AngleOfAttack` (Degrees)
- `ChordLength` (Meters)
- `FreeStreamVelocity` (Meters per second)
- `SuctionSideDisplacement` (Meters)
- **Target Variable:** `SoundLevelDecibels` (Decibels)

## 🚀 Project Architecture

The project is broken down into four main stages:

### 1. ETL Activity (Extract, Transform, Load)

- Loaded the raw CSV dataset into a Spark DataFrame.
- Cleaned the data by removing duplicates and dropping rows with null values.
- Renamed the target column for better readability.
- Stored the cleaned data in the highly optimized `.parquet` format.

### 2. Machine Learning Pipeline

Constructed a sequential PySpark ML Pipeline comprising:

1.  **VectorAssembler**: Combines input features into a single vector column.
2.  **StandardScaler**: Standardizes features by removing the mean and scaling to unit variance.
3.  **LinearRegression**: Trains the model to predict the continuous sound level output.

### 3. Model Evaluation

The pipeline was trained using a 70/30 train-test split (Seed: 42) and evaluated using standard regression metrics:

- **Mean Squared Error (MSE):** ~25.0
- **Mean Absolute Error (MAE):** ~3.91
- **R-Squared ($R^2$):** ~0.50

### 4. Model Persistence

Saved the trained pipeline model to disk (`Final_Project/` directory) for future production use and verified it by loading it back into memory to make predictions on test data.

## 💻 How to Run

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/AbdullahMahmoud23/pyspark-airfoil-noise-prediction.git](https://github.com/AbdullahMahmoud23/pyspark-airfoil-noise-prediction.git)
   cd pyspark-airfoil-noise-prediction
   ```
