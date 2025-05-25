# Dockerfile.mlflow
FROM python:3.9-slim

WORKDIR /app

RUN pip install mlflow psycopg2-binary pymongo[srv] boto3

# Port pour MLflow UI
EXPOSE 5000

# Configuration par défaut (peut être overridé)
ENV MLFLOW_PORT=5000
ENV MLFLOW_BACKEND_STORE_URI=sqlite:///mlruns/mlflow.db
ENV MLFLOW_DEFAULT_ARTIFACT_ROOT=./mlruns

CMD mlflow server \
    --backend-store-uri ${MLFLOW_BACKEND_STORE_URI} \
    --default-artifact-root ${MLFLOW_DEFAULT_ARTIFACT_ROOT} \
    --host 0.0.0.0 \
    --port ${MLFLOW_PORT}
