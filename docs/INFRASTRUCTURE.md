# SUPAA Infrastructure (Backend)

## Cloud Environment: Google Cloud Platform (GCP)
Project ID: `super-power-agents`

## Compute Resources
1.  **Serving (Cloud Run):**
    - Services: `supaa-api`, `tutor-backend`
    - Region: `us-central1`
    - Software: Docker, Python, FastAPI, Gunicorn/Uvicorn.
    - Configuration: Autoscalable stateless containers deployed from `us-docker.pkg.dev`.

## Storage & Databases
- **Relational Database:** Cloud SQL for PostgreSQL.
  - Features: Multi-AZ for high availability, `pgvector` enabled for semantic search.
- **In-Memory Store:** Memorystore for Redis.
  - Role: Session caching, task orchestration queues, high-speed rate limiting.
- **Model Cache (GCS):** `gs://super-power-agents-model-cache/`

## Networking
- **VPC:** `gemma-vpc`
- **Subnet:** `gemma-subnet`
- **Egress & Ingress:** Serverless VPC Access connector to secure backend communication with Cloud SQL and Memorystore.
- API is publicly accessible via the authenticated Cloud Run endpoint.

## Provisioning
- Managed via Terraform located at `infra/terraform/`.
- CI/CD handles automated deployment of `docker-compose` tested images to GCP Artifact Registry, followed by Cloud Run revision updates.
