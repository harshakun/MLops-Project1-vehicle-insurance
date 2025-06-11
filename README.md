# MLOps Project: Vehicle Insurance Claim Prediction

This project implements a complete MLOps pipeline for a machine learning model that predicts whether a vehicle insurance claim will be filed. The pipeline includes data ingestion, validation, transformation, model training, evaluation, deployment, and CI/CD integration using industry-grade tools and services.

## Tech Stack

- Programming Language: Python
- Machine Learning: scikit-learn, pandas, NumPy
- MLOps Tools: Docker, GitHub Actions, DVC, Logging
- Cloud Services: AWS S3 (data and model storage), EC2 (deployment), IAM (role and access management), ECR (Docker image storage)
- Database: MongoDB (for data ingestion and tracking)
- Deployment Framework: Flask or FastAPI


## Pipeline Overview

### Data Ingestion
- Fetches data from MongoDB.
- Stores raw data in the `artifacts/` directory.

### Data Validation
- Validates the schema.
- Checks for missing or invalid values.
- Generates a validation report.

### Data Transformation
- Applies preprocessing such as encoding, scaling, and imputing.
- Saves transformed data for training.

### Model Training
- Trains a classification model using scikit-learn.
- Saves the trained model and performance metrics.

### Model Evaluation
- Evaluates the new model against a previously deployed model (if any).
- Uses metrics like accuracy, precision, recall, and F1-score.

### Model Pusher
- Uploads the final model to AWS S3 or another model registry.
- Updates the model registry with versioning.

## Deployment

- Containerized using Docker.
- Deployed on AWS EC2.
- Uses AWS ECR for storing Docker images.
- The model is served via Flask/FastAPI for prediction.

## CI/CD with GitHub Actions

- Linting and testing on every push.
- Docker build and push to ECR.
- SSH into EC2 and pull the latest image for deployment.

## Run Locally

```bash
# Clone the repository
git clone https://github.com/yourusername/vehicle-insurance-mlops.git
cd vehicle-insurance-mlops

# Set up a virtual environment
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Run the pipeline
python src/pipeline.py

# Run the application
python app.py


