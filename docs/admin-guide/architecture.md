# Architecture

Cloudrock is composed of a several components.

- Cloudrock UI (web client, graphical interface) - React application
- Metal API server - Django/Django REST Framework application implementing the core business logic
- Celery workers - Background processing of tasks
- Celery beat - Scheduling of periodic tasks for background processing
- PostgreSQL database - Storing persistent data, also serves as Celery result store in Kubernetes deployment
- Redis - Tasks queue and result store for Celery (Docker Compose deployment only)
- RabbitMQ - Tasks queue and result store for Celery (Kubernetes deployment only)

![diagram](../assets/components.svg)

