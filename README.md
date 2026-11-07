# MIcroservices-config

# Microservices Configuration Practice 🚀

A dedicated repository to experiment, practice, and implement various configuration management patterns, strategies, and tools for a microservices architecture.

## 🎯 Objectives
- Decouple application configurations from code to enable independent deployments.
- Manage environment-specific behaviors seamlessly.
- Secure sensitive information and secrets.
- Implement dynamic configuration updates without downtime.

---

## 🛠️ Configuration Areas & Practice Roadmap

### 1. Centralized Configuration Management
* **Concept:** Move away from local `application.properties` or `appsettings.json` files embedded in every microservice.
* **Practice:** Set up a Central Configuration Server (such as Spring Cloud Config Server or HashiCorp Consul) that acts as the single source of truth for all environment properties stored in this repository.

### 2. Environment-Specific Profiles
* **Concept:** Adapt service behaviors based on runtime environments.
* **Practice:** Structure YAML/Properties files using profiles (`dev`, `qa`, `staging`, `prod`):
  - `application-dev.yml` (Local databases, debug logging enabled)
  - `application-prod.yml` (Cluster endpoints, optimized connection pools, info/warn logging)

### 3. Dynamic Configuration Refresh (Hot-Reloading)
* **Concept:** Modify configurations (like logging levels, timeouts, or feature flags) without restarting running service instances.
* **Practice:** Implement auto-refresh triggers using webhooks, message brokers (RabbitMQ/Kafka), or Kubernetes ConfigMap watches.

### 4. Secret Management & Security
* **Concept:** Eliminate hardcoded passwords, database URIs, API tokens, and JWT secrets.
* **Practice:** Integrate external secure vaults (like HashiCorp Vault, AWS Secrets Manager, or Kubernetes Secrets) and use encrypted property values (`{cipher}...`).

---

## 📁 Suggested Repository Structure

```text
/
├── config-server/           # Central configuration server module
├── microservices/
│   ├── order-service/       # Sample service pulling config remotely
│   └── user-service/        # Sample service pulling config remotely
└── shared-configs/          # Centralized YAML/Properties files
    ├── application.yml      # Global default properties
    ├── order-service.yml    # Service-specific overrides
    └── order-service-prod.yml # Production-specific profile overrides
