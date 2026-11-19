# Apache Airflow Data Engineering Project

A hands-on Data Engineering project focused on building practical data pipelines and learning workflow orchestration with Apache Airflow.

The long-term goal is to develop an end-to-end E-commerce Data Engineering pipeline, covering data extraction, transformation, storage, orchestration, error handling, monitoring, and testing.

---

## Project Overview

This repository documents the development of a local Apache Airflow environment and the progressive implementation of a real-world data engineering project.

The project follows a milestone-based learning approach. Each milestone introduces practical concepts and implementation techniques used in modern data engineering workflows.

**Current milestone:** Airflow environment setup completed.

---

## Technology Stack

| Technology | Version / Configuration |
|---|---|
| Apache Airflow | 3.3.2 |
| PostgreSQL | 16 |
| Redis | 7.2 |
| Executor | CeleryExecutor |
| Containerization | Docker Compose |
| Development Environment | Windows + Docker Desktop |
| Terminal | PowerShell |

---

## Airflow Architecture

The local environment uses the CeleryExecutor architecture.

The main components are:

| Component | Responsibility |
|---|---|
| API Server | Provides the Airflow web interface and API access. |
| Scheduler | Determines when DAG runs and tasks should execute. |
| DAG Processor | Parses DAG files and processes DAG definitions. |
| Celery Worker | Executes tasks distributed through the Celery broker. |
| Triggerer | Handles deferrable tasks and asynchronous triggers. |
| PostgreSQL | Stores Airflow metadata and execution-related information. |
| Redis | Acts as the Celery message broker. |

### Architecture Flow

```text
                  Airflow UI
                      |
                      v
                 API Server
                      |
                      v
                  Scheduler
                      |
                      v
                DAG Processor
                      |
                      v
                 Redis Broker
                      |
                      v
                Celery Worker
                      |
                      v
                 Task Execution

             PostgreSQL Database
              (Metadata Storage)

                  Triggerer
          (Deferrable Task Handling)
```

---

## Repository Structure

```text
airflow-docker/
|
|-- dags/
|   |-- # Airflow DAG definitions
|
|-- logs/
|   |-- # Generated task execution logs
|
|-- config/
|   |-- # Airflow configuration
|
|-- plugins/
|   |-- # Custom Airflow plugins
|
|-- include/
|   |-- # Supporting project files
|
|-- tests/
|   |-- # Pipeline and DAG tests
|
|-- docker-compose.yaml
|-- .env.example
|-- .gitignore
|-- README.md
```

---

## Getting Started

### Prerequisites

Install the following tools:

- Docker Desktop
- Docker Compose
- Git

Docker Desktop must be running before starting the Airflow environment.

### 1. Clone the Repository

```powershell
git clone <repository-url>
cd airflow-docker
```

### 2. Configure Environment Variables

Create your local environment file from the example:

```powershell
Copy-Item .env.example .env
```

Generate your own secure credentials and replace every placeholder value in `.env`.

Never commit your actual `.env` file.

### 3. Initialize Airflow

Run the initialization service:

```powershell
docker compose up airflow-init
```

Wait until the initialization process completes successfully.

### 4. Start Airflow Services

```powershell
docker compose up -d
```

### 5. Verify Running Services

```powershell
docker compose ps
```

Check that the required services are running and healthy.

### 6. Access the Airflow UI

Open:

http://localhost:8080

Sign in using the administrator username and password configured in your `.env` file.

---

## Learning and Development Roadmap

The project will progressively cover the following areas:

### Phase 1 — Environment and Airflow Fundamentals

- Docker-based Airflow environment setup
- Airflow architecture
- DAG fundamentals
- Tasks and task dependencies
- Scheduling and execution

### Phase 2 — Data Extraction

- Python-based API integration
- HTTP requests and response handling
- API pagination
- Data extraction patterns
- Handling external API failures

### Phase 3 — Data Transformation

- Data validation
- Data cleaning
- Python transformations
- Handling missing and inconsistent data
- Structured data processing

### Phase 4 — Data Storage

- PostgreSQL integration
- Database connections
- SQL operations
- Data loading strategies
- Incremental data loading

### Phase 5 — Reliability and Orchestration

- Task retries
- Retry delays
- Failure handling
- Timeouts
- Idempotency
- Backfill and catchup
- Scheduling strategies

### Phase 6 — Monitoring and Testing

- Airflow logs
- DAG testing
- Task monitoring
- Error tracking
- Pipeline validation
- Automated testing

### Phase 7 — End-to-End E-commerce Pipeline

Build and orchestrate an end-to-end E-commerce data pipeline integrating the concepts developed throughout the project.

---

## Project Status

| Milestone | Status |
|---|---|
| Development environment setup | Completed |
| Docker Compose configuration | Completed |
| PostgreSQL integration | Completed |
| Redis integration | Completed |
| CeleryExecutor setup | Completed |
| Airflow UI access | Completed |
| First DAG implementation | Pending |
| API data extraction | Pending |
| Data transformation | Pending |
| PostgreSQL data pipeline | Pending |
| Monitoring and testing | Pending |

This is an ongoing learning and development project. The current environment is intended for local development and experimentation, not production deployment.

---

## Security Practices

- Keep `.env` out of version control.
- Never publish passwords, tokens, or generated secrets.
- Use `.env.example` to document required environment variables.
- Use strong credentials for local services.
- Do not expose development services publicly.
- Review configuration changes before committing them.

---

## Progress Tracking

Development progress will be documented through Git commits and milestone tags.

Each major implementation stage will have its own Git history so that earlier versions of the project can be inspected independently.

---

## License

License not yet specified.
