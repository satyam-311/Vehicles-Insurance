# 🚗 Vehicle Insurance ML Project – End-to-End MLOps

A production-ready **Machine Learning + MLOps** pipeline designed to impress recruiters and showcase real-world engineering skills. This project implements everything from **data ingestion → model training → cloud storage → CI/CD → deployment**.

---

## ⭐ Project Highlights

* **Complete MLOps Workflow** with industry standards
* **Automated Data Pipeline** (Ingestion, Validation, Transformation)
* **MongoDB → AWS S3 → EC2 → ECR** integration
* **CI/CD Pipeline using GitHub Actions**
* **Dockerized FastAPI/Flask App** with full Prediction Pipeline
* **Modular, Scalable Code Structure** for production use

---

# 🏗 Project Architecture

```
Template → Virtual Environment → MongoDB → Data Pipeline → AWS Setup → CI/CD → Deployment
```

---

# 📁 Project Setup

## 1️⃣ Generate Project Template

Run:

```bash
python template.py
```

This creates the full production-ready folder structure.

## 2️⃣ Local Package Setup

Configure:

* `setup.py`
* `pyproject.toml`

These enable local package installation using `pip install -e .`.

Refer to **crashcourse.txt** for detailed explanation.

---

# 🐍 Virtual Environment Setup

```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
pip list
```

Ensures your local packages and dependencies are installed.

---

# 🍃 MongoDB Atlas Setup

1. Create project in MongoDB Atlas
2. Deploy **M0 cluster**
3. Create DB user (username + password)
4. Add network IP: `0.0.0.0/0`
5. Copy connection string (Python driver)
6. Create `notebook/mongoDB_demo.ipynb`
7. Upload dataset to notebook folder
8. Push dataset → MongoDB using your notebook
9. Verify in **Browse Collections**

---

# 📝 Logging, Exceptions & Notebooks

* Implement **logger.py** → test in `demo.py`
* Implement **exception.py** → test in `demo.py`
* Added **EDA + Feature Engineering** notebooks

---

# 📥 Data Ingestion Module

Inside `src/`:

* Add constants in `constants/__init__.py`
* Add MongoDB connection logic in `configuration/mongo_db_connections.py`
* Implement **data_access** layer to fetch DB data → DataFrame
* Create config classes in `entity/config_entity.py`
* Create artifact classes in `entity/artifact_entity.py`
* Implement ingestion logic in `components/data_ingestion.py`
* Add ingestion stage to **training pipeline**

Run:

```bash
$env:MONGODB_URL="your_url_here"
python demo.py
```

---

# 🧪 Data Validation, Transformation & Model Trainer

### Files Added:

* `utils/main_utils.py`
* `config/schema.yaml`
* `entity/estimator.py`

### Components Implemented:

* **Data Validation** – Schema check, missing values, drift
* **Data Transformation** – Scalers, pipelines, preprocessing
* **Model Trainer** – Train & save model artifact

---

# ☁️ AWS Setup (S3, IAM, Access Keys)

### Steps:

1. Create IAM user (AdministratorAccess)
2. Generate **Access Key + Secret Key**
3. Set environment variables:

```powershell
$env:AWS_ACCESS_KEY_ID="xxx"
$env:AWS_SECRET_ACCESS_KEY="yyy"
```

4. Add keys to constants
5. Create S3 bucket:

```
Name: my-model-mlopsproj
Region: us-east-1
Public Access: OFF
```

6. Implement `aws_connection.py`
7. Implement `aws_storage/` for pull/push to S3
8. Add `s3_estimator.py` for model registry operations

---

# 📊 Model Evaluation & Pusher

* Evaluate old model vs new model
* Compare performance
* Apply threshold `0.02`
* Push new model to S3 registry

---

# 🔮 Prediction Pipeline & Web App Setup

* Add prediction logic
* Add `app.py`
* Add `static/` and `templates/` directories

---

# 🐳 Docker + GitHub Actions CI/CD

### 1. Docker Setup

* Create Dockerfile
* Add `.dockerignore`

### 2. GitHub Actions

Create workflow:

```
.github/workflows/aws.yaml
```

Used for:

* Build Docker Image
* Push to ECR
* Deploy on EC2

### 3. AWS Resources Required

* IAM user: `usvisa-user`
* ECR repository: `vehicleproj`
* EC2 machine: Ubuntu 24.04
* Install Docker on EC2
* Connect EC2 with GitHub as **Self Hosted Runner**

---

# 🚀 Deployment

After CI/CD completes:

1. Open EC2 Security Group
2. Add inbound rule:

```
Type: Custom TCP
Port: 5080
Source: 0.0.0.0/0
```

3. Visit app at:

```
http://<EC2_PUBLIC_IP>:5080
```

Model training also available at:

```
/training
```

---

# 🎯 Final Outcome

This project demonstrates:

* Full **end-to-end MLOps lifecycle**
* Real-world **cloud engineering**
* Production-grade **machine learning pipeline**
* Professional **CI/CD workflow**
* Containerized **deployable ML system**

A perfect showcase to impress recruiters and companies looking for ML Engineers, Data Engineers, or MLOps Engineers.

---

# 🧑‍💻 Author

**Satyam Mishra**
AIML Engineer | MLOps Learner | NLP & ML Practitioner

---
