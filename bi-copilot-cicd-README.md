# BI Copilot CI/CD Pipeline

**Bastion-proxied deployment pipeline with pre-migration backups and selective service restarts.**

## Overview

This is the deployment pipeline for the BI Copilot production system, built to deploy safely into a private EC2 instance that has no direct public access. Every deploy goes through a bastion host, takes a database backup before running migrations, and restarts only the services affected by the change — rather than tearing down the full stack on every push.

## Tech Stack

- **GitHub Actions** — CI/CD orchestration
- **EC2 (private, bastion-accessed)** — production host
- **Docker Compose** — service orchestration on the target host

## How It Works

1. On push to the deploy branch, GitHub Actions builds and runs checks.
2. The pipeline connects to the private EC2 instance through a bastion host (no direct public exposure of the production box).
3. Before applying any database migrations, a `pg_dump` backup is taken so a bad migration can be rolled back.
4. Deployment uses `git reset --hard` on the target to guarantee a clean, reproducible state matching the pipeline's commit.
5. Only the Docker Compose services impacted by the change are restarted, minimizing downtime for unrelated services.

## Getting Started

### Prerequisites

- GitHub repository with Actions enabled
- SSH access configured for the bastion host and the private EC2 target
- Docker & Docker Compose on the target instance
- PostgreSQL client tools on the target (for `pg_dump`)

### Configuration

Set the following repository secrets in GitHub Actions:

```
BASTION_HOST
BASTION_SSH_KEY
TARGET_HOST
TARGET_SSH_KEY
DB_CONNECTION_STRING
```

### Deploy

Pushing to the configured deploy branch triggers the pipeline automatically. Manual runs are available via the Actions tab (`workflow_dispatch`).

## Safety Features

- Pre-migration backups mean a failed migration is always recoverable.
- Bastion-only access keeps the production database host off the public internet.
- Selective restarts avoid unnecessary downtime on unaffected services.

## License

MIT
