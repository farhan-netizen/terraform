# terraform

A hands-on learning journey from Terraform fundamentals to automated infrastructure management and Platform Engineering.

**Current constraint:** No cloud subscription. Initial labs will use local resources and free tools.

## Table of Contents

- [Goal](#goal)
- [Learning Objectives](#learning-objectives)
- [Roadmap](#roadmap)
- [Learning Principles](#learning-principles)
- [Definition of Success](#definition-of-success)

---

## Goal

Build practical Terraform skills to design, provision, validate, secure, and maintain infrastructure using Infrastructure as Code (IaC).

The focus is on understanding how Terraform works and applying it to real-world Platform Engineering workflows—not just memorizing HCL syntax.

## Learning Objectives

By the end of this journey, I aim to be able to:

- Write Terraform configurations using HCL, providers, resources, and data sources.
- Manage variables, outputs, expressions, dependencies, and resource lifecycles.
- Understand state management, backends, locking, drift detection, and state operations.
- Build reusable modules and maintainable project structures.
- Implement validation, testing, security checks, and policy-as-code.
- Integrate Terraform with Git, CI/CD pipelines, and approval workflows.
- Apply Terraform principles to cloud infrastructure, Kubernetes, and Platform Engineering.

## Roadmap

| Phase | Focus | Practical Outcome |
| --- | --- | --- |
| 1 | Foundations | Create a local file using Terraform |
| 2 | HCL and Resources | Build configurable local resources |
| 3 | State Management | Inspect state, detect changes, practise state operations |
| 4 | Modules | Build and reuse Terraform modules |
| 5 | Quality and Security | Automate validation and policy checks |
| 6 | Git and CI/CD | Build a Terraform validation pipeline |
| 7 | Advanced Terraform | Practise complex configurations and troubleshooting |
| 8 | Cloud and Platform Engineering | Provision cloud and Kubernetes infrastructure when access is available |

### Phase 1 — Foundations

- Infrastructure as Code and Terraform architecture
- HCL syntax, providers, resources, and data sources
- `init`, `plan`, `apply`, and `destroy`
- Formatting and validation

**Lab:** Create a local file using the `local` provider.

### Phase 2 — HCL and Resource Management

- Variables, outputs, locals, and functions
- Expressions and resource dependencies
- `count`, `for_each`, `depends_on`, and `lifecycle`
- Conditional expressions and dynamic blocks

**Lab:** Build a configurable project with multiple local resources.

### Phase 3 — State Management

- Terraform state and resource addressing
- Desired state, actual state, and drift detection
- State operations and resource imports
- Backends, locking, backups, and recovery concepts

**Lab:** Inspect state changes and practise safe local state operations.

### Phase 4 — Reusable Modules

- Module structure and composition
- Input/output contracts and version constraints
- Environment separation and naming conventions

**Lab:** Build a reusable module and consume it from a root configuration.

### Phase 5 — Quality and Security

- `terraform fmt` and `terraform validate`
- Testing and plan review
- TFLint and Checkov
- OPA, Rego, and policy-as-code
- Secrets management and least privilege

**Lab:** Create automated validation and policy checks without cloud resources.

### Phase 6 — Git and CI/CD

- Git, branches, pull requests, and code reviews
- Automated formatting and validation
- Plan review and approval gates
- Jenkins or GitHub Actions integration
- Pipeline credentials and security

**Lab:** Build a CI workflow that validates Terraform changes.

### Phase 7 — Advanced Terraform

- Provider aliases and module composition
- Dependency graph and execution behaviour
- Workspaces and backend migration concepts
- Debugging, failure analysis, and operational practices

**Lab:** Build a multi-module project with automated checks.

### Phase 8 — Cloud and Platform Engineering

*Planned for when suitable cloud access becomes available.*

- Cloud networking, compute, and security
- Virtual networks, subnets, and security rules
- Kubernetes clusters and node pools
- Remote state and cloud identity
- Infrastructure for containerized applications and internal developer platforms

**Lab:** Provision a cloud network and Kubernetes infrastructure when an appropriate environment is available.

## Learning Principles

- Learn one concept at a time.
- Verify commands and outputs before documenting them as tested.
- Include prerequisites, expected results, common errors, and troubleshooting.
- Prefer small, reproducible experiments.
- Never publish credentials, sensitive state, or unauthorized proprietary code.
- Clearly distinguish locally tested examples from cloud-tested implementations.

## Definition of Success

- [ ] Write and troubleshoot Terraform configurations independently.
- [ ] Explain Terraform's workflow, dependency graph, and state management.
- [ ] Build reusable modules and automated quality checks.
- [ ] Integrate Terraform into a Git-based CI/CD workflow.
- [ ] Publish a documented portfolio of practical projects.
- [ ] Extend these skills to cloud and Kubernetes infrastructure.

## Repository Status

This repository is a work in progress. It starts with local, reproducible labs and will expand into cloud-based Platform Engineering scenarios as suitable resources become available.

