# Spring Cloud Config Repository

This repository contains centralized configuration for the Fitness Tracker microservices application.

## Configuration Files

- `application.yml` - Common configuration for all services
- `user-service.yml` - User service specific configuration
- `activity-service.yml` - Activity service specific configuration
- `ai-service.yml` - AI service specific configuration
- `api-gateway.yml` - API Gateway specific configuration
- `eureka-server.yml` - Eureka Server specific configuration

## Environment Variables

The configuration files use environment variables that are injected via Kubernetes secrets and configmaps:

### Database (PostgreSQL - RDS)
- `SPRING_DATASOURCE_URL`
- `SPRING_DATASOURCE_USERNAME`
- `SPRING_DATASOURCE_PASSWORD`

### MongoDB
- `MONGODB_URI`
- `MONGODB_DATABASE`

### RabbitMQ (Amazon MQ)
- `RABBITMQ_HOST`
- `RABBITMQ_PORT`
- `RABBITMQ_USERNAME`
- `RABBITMQ_PASSWORD`

### Keycloak
- `KEYCLOAK_ISSUER_URI`

### Eureka
- `EUREKA_CLIENT_SERVICEURL_DEFAULTZONE`

### AI Service
- `GEMINI_API_KEY`

## Usage with Spring Cloud Config Server

The Config Server is configured to read from this Git repository. Each service will fetch its configuration on startup by contacting the Config Server at `http://config-server:8888`.

## Profiles

Currently using `prod` profile for Kubernetes deployment.
