# MLOps End-to-End Machine Learning Pipeline

This project demonstrates a complete MLOps lifecycle implementation, from data ingestion to CI/CD deployment on AWS using Docker, ECR, EC2, and GitHub Actions. It includes experiment tracking, modular pipeline development, model training, and cloud deployment.

# Project Overview
The system builds a machine learning pipeline for classification tasks using structured data and follows MLOps best practices:

Modular coding structure
MongoDB data storage
Logging and custom exception handling
DVC-based pipeline tracking
ML model training & evaluation
AWS cloud deployment (ECR + EC2)
CI/CD using GitHub Actions

# Tech Stack
Python 3.10
Scikit-learn
FastAPI
MongoDB Atlas
MLflow (experiment tracking)
DVC (data versioning)
Docker
AWS (EC2, ECR, S3, IAM)
GitHub Actions (CI/CD)

# ML Pipeline Workflow
## 1️ Project Setup
Project template creation using template.py
Setup setup.py and pyproject.toml for local package imports
Virtual environment setup using Conda
Dependency installation via requirements.txt
## 2️ MongoDB Setup
MongoDB Atlas cluster creation
Data upload from notebook
Connection string stored in environment variables
## 3️ Logging & Exception Handling
Custom logger implementation
Custom exception class
Tested using demo.py
## 4️ Data Ingestion
MongoDB connection established
Data fetched and converted to DataFrame
Stored as artifacts for pipeline tracking
## 5️ Data Validation & Transformation
Schema validation using schema.yaml
Missing value & data consistency checks
Feature engineering and transformation pipeline
## 6️ Model Training
## 7️ Model Evaluation & Pusher
Model comparison with previous version
Best model pushed to AWS S3 bucket
## 8️ Experiment Tracking
MLflow used for tracking:
Parameters
Metrics
Artifacts
Models
Local + remote tracking via DagsHub
## 9️ DVC Pipeline
DVC is used to track pipeline stages:
data_ingestion
data_preprocessing
feature_engineering
model_building
model_evaluation
## 10 FastAPI Prediction App
Web interface using FastAPI
HTML templates + static files
User input → prediction output

## AWS Setup
Services Used:
IAM (user creation)
S3 (model storage)
ECR (Docker image registry)
EC2 (deployment server)
Deployment Flow:
Create IAM user + permissions
Create S3 bucket
Create ECR repository (vehicleproj)
Launch EC2 instance (Ubuntu)
Install Docker on EC2
Configure GitHub self-hosted runner
Push Docker image to ECR
Deploy container on EC2
CI/CD Pipeline (GitHub Actions)

## Pipeline performs:
Code checkout
Docker build
Push image to AWS ECR
Deploy to EC2 via self-hosted runner
Application Access

## After deployment:

http://<EC2-PUBLIC-IP>:5000
/ → Prediction UI
/train → Model training pipeline

## Environment Variables

Required secrets in GitHub:
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_DEFAULT_REGION
ECR_REPO
MONGODB_URL