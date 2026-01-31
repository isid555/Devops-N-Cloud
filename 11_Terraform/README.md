i# Terraform Basics

## What is Terraform?

Terraform is an **Infrastructure as Code (IaC)** tool developed by HashiCorp. It allows you to define, provision, and manage infrastructure using **declarative configuration files** instead of manually configuring resources through cloud dashboards or scripts.

In simple terms:
- You describe **what infrastructure you want**
- Terraform determines **how to create or modify it**

The result is infrastructure that is **reproducible, version-controlled, auditable, and scalable**.

---

## Why Terraform Exists

Manual infrastructure management does not scale. It leads to:
- Configuration drift
- Human errors
- Inconsistent environments
- Poor documentation

Terraform solves this by:
- Treating infrastructure as code
- Enabling repeatable and predictable deployments
- Maintaining consistency across environments (dev, staging, prod)
- Acting as a single source of truth for infrastructure state

This is foundational DevOps practice, not a nice-to-have.

---

## What Terraform Is Used For

Terraform is used to provision and manage:
- Cloud infrastructure (VMs, VPCs, subnets)
- Databases (RDS, Cloud SQL, DynamoDB)
- Networking (load balancers, firewalls, DNS)
- IAM resources (users, roles, policies)
- Kubernetes clusters and objects
- SaaS resources (GitHub repos, monitoring tools)

If a platform exposes an API, Terraform can likely manage it.

---

## Core Concepts

### Infrastructure as Code (IaC)
Infrastructure is defined in `.tf` files using **HCL (HashiCorp Configuration Language)**.  
HCL is declarative, human-readable, and purpose-built for infrastructure.

---

### Providers
Providers are plugins that allow Terraform to interact with external systems.

Examples:
- AWS
- Azure
- Google Cloud
- Kubernetes
- GitHub

Terraform itself is platform-agnostic; providers handle the integrations.

---

### Resources
Resources represent **actual infrastructure components** such as:
- Virtual machines
- Databases
- Storage buckets
- IAM roles

Each resource describes the desired end state, not the execution steps.

---

### State
Terraform maintains a **state file** that maps:
- Terraform configuration → Real-world infrastructure

State enables Terraform to:
- Detect existing resources
- Calculate changes
- Avoid unnecessary recreation

State is critical. In production systems, it should be stored remotely (e.g., S3 + DynamoDB, Terraform Cloud).

---

### Terraform Workflow

Terraform follows a predictable lifecycle:

1. `terraform init` – Initialize providers and backend
2. `terraform plan` – Show what will change
3. `terraform apply` – Apply the planned changes
4. `terraform destroy` – Remove managed infrastructure

This workflow enforces review and reduces deployment risk.

---

## Declarative vs Imperative

- Imperative: *Create a VM, then attach storage, then open ports*
- Declarative: *I want a VM with storage and open ports*

Terraform focuses on **desired state**, enabling:
- Idempotent operations
- Safe re-execution
- Automatic dependency handling

---

## Advantages of Terraform

- Cloud-agnostic
- Version-control friendly
- Strong dependency graph
- Predictable and repeatable deployments
- Supports immutable infrastructure practices

This makes Terraform suitable for both startups and large enterprises.

---

## What Terraform Is Not

- Not a configuration management tool (use Ansible, Chef, etc.)
- Not a CI/CD system
- Not cloud-specific

Terraform provisions infrastructure. Other tools configure applications on top of it.

---

## Typical Use Case

1. Define infrastructure in `.tf` files
2. Store code in a Git repository
3. Run `terraform plan` in CI
4. Review changes
5. Apply changes after approval
6. Maintain environments reliably

Infrastructure becomes deterministic and auditable.

---

## Summary

Terraform transforms infrastructure from a fragile, manual process into a **repeatable engineering system**.  
If you are building scalable, production-grade systems, Terraform is not optional—it is foundational.

Infrastructure should be boring, predictable, and automated. Terraform makes that possible.

