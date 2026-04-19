# SUPAA - Multi-Agent Orchestration Platform (Backend)

SUPAA is the intelligent orchestration layer for multi-agent AI systems, built for scalability and performance on Google Cloud Platform. This repository contains the backend services and infrastructure definitions.

## Repository Structure

- `api/`: FastAPI backend service.
  - `app/`: Application logic.
  - `Dockerfile`: Container definition for backend.
  - `requirements.txt`: Python dependencies.
- `infra/terraform/`: GCP Infrastructure as Code.
- `docker-compose.yml`: Local development setup (backend focus).

## Engineering Documentation Standard
All engineers contributing to this repository must follow the [SUPAA Engineering Documentation Standard](https://github.com/SuperAgentsCompany/documentations/blob/main/engineering/standards.md). Ensure all major changes, how-to instructions, progress updates, and metrics are documented.

## Getting Started

### Local Development

To start the backend locally using Docker Compose:

```bash
docker-compose up --build
```

- API will be available at `http://localhost:8000`

### Infrastructure Deployment

1. Initialize Terraform:
   ```bash
   cd infra/terraform
   terraform init
   ```

2. Plan the deployment:
   ```bash
   terraform plan -var="project_id=YOUR_PROJECT_ID" -var="db_password=YOUR_DB_PASSWORD"
   ```

3. Apply the changes:
   ```bash
   terraform apply -var="project_id=YOUR_PROJECT_ID" -var="db_password=YOUR_DB_PASSWORD"
   ```

## Tech Stack

- **Backend:** Python, FastAPI, SQLAlchemy, pgvector.
- **Data:** PostgreSQL, Redis.
- **Cloud:** GCP (Cloud Run, Cloud SQL, Memorystore, Cloud Storage).
