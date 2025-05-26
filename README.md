# MLflow Server Setup

This repository provides a ready-to-use [MLflow](https://mlflow.org/) server deployment using Docker Compose, with MySQL as the backend store and MinIO (S3-compatible) as the artifact store.

## Services

- **MLflow 2.11.1**  
   Experiment tracking server deployed via Docker, providing a user-friendly UI and REST API.
- **ARM64 Platform Support**  
   Compatible with ARM64 architectures for broader deployment options.

## Getting Started

### 1. Deploy Prerequisites
Use these prebuilt Dockerized services as prerequisites:
- [MySQL instance](https://github.com/furiatona/database-docker)
- [MinIO instance](https://github.com/furiatona/minio-storage)

Then, create the required database and S3 bucket

### 2. Configure Environment Variables

Copy `.env.sample` to `.env` and update values as needed:

```bash
cp .env.sample .env
```

**Required variables:**
```env
MYSQL_USER=your_mysql_user
MYSQL_PASSWORD=your_mysql_password
MYSQL_HOST=your_mysql_host
MYSQL_DATABASE=your_mlflow_db

MINIO_BUCKET=your_minio_bucket
MINIO_URL=http://your_minio_host:9000
MINIO_ACCESS_KEY=your_minio_access_key
MINIO_SECRET_KEY=your_minio_secret_key
```

### 3. Start the Stack

```bash
docker compose up -d
```

### 4. Access MLflow UI:

Open [http://localhost:5500](http://localhost:5500) in your browser.

## Networks

- `mlflownetwork` — Isolated bridge network for MLflow

## Resource Limits

MLflow is configured with memory and CPU limits for efficient local development. You can customize these in `docker-compose.yml` as needed.

---

**License:** MIT  
**Author:** [furiatona](https://github.com/furiatona)