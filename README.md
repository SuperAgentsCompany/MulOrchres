# SUPAA - Multi-Agent Orchestration Platform

SUPAA is the intelligent orchestration layer for multi-agent AI systems, built for scalability and performance on Google Cloud Platform.

## Repository Structure

- `api/`: FastAPI backend service.
  - `app/`: Application logic.
  - `Dockerfile`: Container definition for backend.
  - `requirements.txt`: Python dependencies.
- `frontend/`: Next.js (React) frontend.
  - `src/app/`: Next.js App Router pages and layouts.
  - `Dockerfile`: Container definition for frontend.
  - `package.json`: Node.js dependencies.
- `infra/terraform/`: GCP Infrastructure as Code.
- `docker-compose.yml`: Local development setup.

## Getting Started

### Local Development

To start the entire stack locally using Docker Compose:

```bash
docker-compose up --build
```

- API will be available at `http://localhost:8000`
- Frontend will be available at `http://localhost:3000`

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
- **Frontend:** Next.js, TypeScript, Vanilla CSS.
- **Data:** PostgreSQL, Redis.
- **Cloud:** GCP (Cloud Run, Cloud SQL, Memorystore, Cloud Storage).
