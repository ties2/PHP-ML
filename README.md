# Enterprise Machine Learning in PHP

[![PHP Version](https://img.shields.io/badge/PHP-8.2%2B-blue.svg)](https://php.net/)
[![Library](https://img.shields.io/badge/Library-PHP--ML-orange.svg)](https://php-ml.readthedocs.io/)
[![Architecture](https://img.shields.io/badge/Architecture-MLOps--Standard-brightgreen.svg)]()

Implement Machine Learning lifecycle and MLOps architectural patterns natively in PHP.

While Python dominates the ML space, many enterprise backends run on PHP. This project illustrates how to decouple data processing, model training, and API serving using a standardized MLOps structure within a PHP ecosystem.

## 🧠 Models Implemented
* **K-Nearest Neighbors (KNN):** Used for categorical classification (e.g., Iris Dataset).
* **Support Vector Regressor (SVR):** Used for continuous variable prediction (e.g., Wine Quality).

## 🏗 Architecture & MLOps Principles
This repository strictly follows MLOps best practices by decoupling the pipeline:

1. **Training Pipeline (`src/Training/`)**: Ingests `CSV` datasets, utilizes Stratified Random Splitting to ensure representative test/train sets, trains the model, and serializes the state to disk.
2. **Serving Layer (`src/Serving/`)**: A lightweight API endpoint that deserializes the pre-trained model into memory to provide low-latency predictions via HTTP POST.
3. **Containerization (`deployment/`)**: Dockerized environment ensuring seamless execution without local PHP configuration.

## 🚀 Quick Start

### Option 1: Run via Docker (Recommended)
```bash
# Build the image
docker build -t php-mlops -f deployment/Dockerfile .

# Run the API server
docker run -p 8000:8000 php-mlops