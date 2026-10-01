# 🚗 Vehicle Insurance Prediction MLOps Project

##  Project Overview

This project showcases a professional, end-to-end **Machine Learning Operations (MLOps)** pipeline for predicting **vehicle insurance purchase intent**.

We’ve built a robust and scalable system that automates every step — from data ingestion to model deployment — using modern MLOps tools and **AWS cloud services**. The goal is to provide a solid foundation for a **production-ready ML solution**.

---

## ⚙️ Key MLOps Features and Technologies

### 📦 Project Structure and Packaging
- **Project Template**: A custom script `template.py` is used to auto-generate the project folder structure using best practices.
- **Package Management**: Managed via `setup.py` and `pyproject.toml`, making the project pip-installable and dependency-resilient.

---

### 💾 Data Management
- **MongoDB Atlas**: Serves as the centralized database for raw insurance data.
- **Data Ingestion Pipeline**: Connects to MongoDB, fetches data, and stores it in a feature store for downstream processing.
- **Data Validation**: Uses `schema.yaml` to validate incoming data structure and types before processing.

---

### 📊 Model Training Pipeline
- **Modular Components**:
  - `Data Ingestion`
  - `Data Validation`
  - `Data Transformation`
  - `Model Trainer`
  - `Model Evaluation`
  - `Model Pusher`
- **Data Transformation**: Includes preprocessing, feature engineering, and class balancing using **SMOTEENN**.
- **Model Training**: Trains a `RandomForestClassifier`, serializes the model for later use.
- **Model Evaluation**: Compares new models with the latest one in production (from S3). Promotes only better-performing models.

---

### ☁️ Cloud Integration with AWS
- **S3**: Used as the central model registry.
- **IAM Roles**: Fine-grained access control with secure credentials.
- **Environment Variables**: MongoDB and AWS credentials are securely managed through `.env` and GitHub secrets.

---

### 🚀 CI/CD Automation
- **GitHub Actions**: Automates CI/CD pipeline on every `git push` to the `main` branch.
- **Dockerization**: The project is containerized for consistent environments across dev, staging, and prod.
- **Amazon ECR**: Stores Docker images in a secure, scalable container registry.
- **Self-Hosted Runner**: Deployed on an EC2 instance to manage the full deployment pipeline.

---

### 🌐 Live Application and Prediction
- **FastAPI**: Serves the ML model with a lightweight, high-performance API.
- **Prediction Pipeline**:
  - Receives input via an HTML form
  - Applies preprocessing
  - Returns prediction in real-time

Application runs on:  
```
http://18.212.216.84:8000
```

---

## 🛠️ How to Run This Project

### 1. Clone the Repository
```bash
git clone https://github.com/rahuljat27/Vehicle_Insurence_MLOPS.git
cd Vehicle_Insurence_MLOPS
```

### 2. Setup MongoDB and AWS
- Create a MongoDB Atlas cluster
- Create an AWS S3 bucket
- Set credentials as environment variables:

```bash
export MONGODB_URL="your-mongodb-connection-string"
export AWS_ACCESS_KEY_ID="your-aws-access-key"
export AWS_SECRET_ACCESS_KEY="your-aws-secret-key"
export AWS_DEFAULT_REGION="your-region"
export ECR_REPO="your-ecr-repo-name"
```

### 3. Run the MLOps Pipeline
Push to `main` branch:

```bash
git add .
git commit -m "trigger pipeline"
git push origin main
```

This triggers the entire CI/CD pipeline:
- Builds and pushes Docker image to ECR
- Deploys model to EC2 via GitHub Actions

---

## 📍 Access the Application

Once deployed, open your browser and go to:

```
http://<your-ec2-public-ip>:8000
```

Use the HTML form to input features and get real-time predictions.

---

## 📁 Project Structure

```
vehicle_insurance_mlops/
├── config/
├── components/
├── pipelines/
├── templates/
├── artifacts/
├── docker/
├── .github/workflows/
├── schema.yaml
├── Dockerfile
├── app.py
├── requirements.txt
├── setup.py
├── pyproject.toml
└── README.md
```

---

## 📌 Future Enhancements
- Add monitoring and logging with **Prometheus + Grafana**
- Set up **automated rollback** on model degradation
- Integrate **feature store** with Feast
- Add **unit tests** and coverage reports to CI

---

## 📧 Contact

**Author:** Abhishek Choudhary 
📬 [LinkedIn](https://www.linkedin.com/in/abhishek-c-1028i/)  
📁 [GitHub](https://github.com/AbhishekChfin)

---

## 📜 License

This project is licensed under the MIT License.
