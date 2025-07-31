---
short_title: CIRRUS Overview
---

![CIRRUS](../../media/CIRRUS_Logo_NCARBlue.png#only-light){width="640"}
![CIRRUS](../../media/CIRRUS_Logo_NCAR_DarkTheme.png#only-dark){width="640"}

# CIRRUS

**CIRRUS** (Cloud Infrastructure for Remote Research, Universities, and Scientists) is a Kubernetes-based cloud platform hosted at NSF NCAR. It provides flexible, scalable compute resources that complement traditional HPC systems, public cloud services, and local infrastructure.

---

## Getting Started Workflows

Choose your path based on your needs and experience level:

| **Basic Users** | **Advanced Users** |
|-----------------|-------------------|
| **1. Learn the Basics** | **1. Review Architecture** |
| Start with [CIRRUS Overview](#platform-overview) | Understand [Platform Overview](#platform-overview) and [Core Services](#core-services) |
| **2. Understand Team Process** | **2. Plan Your Deployment** |
| Review [Team Interaction](../02-interact-with-cirrus-team/agile.md) and [Creating Tickets](../02-interact-with-cirrus-team/create-tickets.md) | Study [Adding Applications](../03-deploying-applications/additions.md) and [Container Registry](../04-container-registry/index.md) |
| **3. Explore Services** | **3. Set Up CI/CD** |
| Try [JupyterHub](../06-jupyter-on-cirrus/jupyterhub.md) for interactive computing | Configure [GitHub Actions](../05-github-actions/scale-sets.md) and [Secrets Management](../07-secret-manager/openbao.md) |
| **4. Request Access** | **4. Deploy Applications** |
| Submit a [service request](../02-interact-with-cirrus-team/create-tickets.md) | Use [GitOps workflow](#gitops-deployment) with Helm charts |

---

## Documentation Guide

This documentation is organized into focused sections to help you find what you need:

| Section | What You'll Find | When to Use |
|---------|------------------|-------------|
| **[Introduction](index.md)** | Platform overview, services, and hardware specs | Start here to understand CIRRUS capabilities |
| **[Interact with CIRRUS Team](../02-interact-with-cirrus-team/)** | | |
| └ [Agile Methodology](../02-interact-with-cirrus-team/agile.md) | How the team works and manages requests | Understand our development process |
| └ [Create Tickets](../02-interact-with-cirrus-team/create-tickets.md) | How to submit requests and report issues | Need help or want to request services |
| **[Deploying Applications](../03-deploying-applications/)** | | |
| └ [Creating Containers](../03-deploying-applications/containerize.md) | Step-by-step containerization guide | New to containers or Docker |
| └ [Adding Applications](../03-deploying-applications/additions.md) | GitOps deployment with Helm charts | Ready to deploy your application |
| **[Container Registry](../04-container-registry/)** | | |
| └ [Harbor Overview](../04-container-registry/index.md) | Container registry introduction | Store and manage container images |
| └ [Image Management](../04-container-registry/image-mgmt.md) | Push/pull images, CLI usage | Work with container images |
| └ [Vulnerability Scanner](../04-container-registry/vulnerability-scan.md) | Security scanning for images | Ensure image security |
| **[GitHub Actions](../05-github-actions/)** | | |
| └ [Runner Scale Sets](../05-github-actions/scale-sets.md) | Automated CI/CD setup | Automate builds and deployments |
| └ [Best Practices](../05-github-actions/best-practices.md) | Security and operational guidelines | Secure your CI/CD pipelines |
| **[Jupyter on CIRRUS](../06-jupyter-on-cirrus/)** | | |
| └ [JupyterHub](../06-jupyter-on-cirrus/jupyterhub.md) | Interactive computing environment | Data analysis and research |
| └ [Conda Environments](../06-jupyter-on-cirrus/conda-envs.md) | Custom Python environments | Manage dependencies |
| └ [GPU Usage](../06-jupyter-on-cirrus/jhub-gpu.md) | GPU computing with PyTorch/TensorFlow | Machine learning and AI workloads |
| └ [Dask Integration](../06-jupyter-on-cirrus/jhub-dask.md) | Distributed computing | Scale computations across nodes |
| └ [Binder](../06-jupyter-on-cirrus/binderhub.md) | Reproducible research environments | Share interactive notebooks |
| **[Secret Manager](../07-secret-manager/)** | | |
| └ [OpenBao](../07-secret-manager/openbao.md) | Secure credential storage | Manage API keys and secrets |
| **[Service Level Agreements](../08-service-level-agreements/)** | | |
| └ [SLAs](../08-service-level-agreements/slas.md) | Support levels and response times | Understand service commitments |

---

## Platform Overview

### Kubernetes Foundation

CIRRUS is built on **Kubernetes (K8s)**, the industry-standard container orchestration platform. Kubernetes provides:

- **High availability** through automatic failover and load balancing
- **Self-healing** infrastructure that automatically replaces failed components
- **Scalable workloads** that can grow and shrink based on demand
- **Shared services** like networking, storage, and security that new applications can leverage immediately

This resilient, open-source foundation makes CIRRUS ideal for hosting research applications, data analysis workflows, and collaborative tools.

### Container Technology

CIRRUS applications run in **containers** - lightweight, portable packages that include everything needed to run an application. Containers offer:

- **Consistent environments** across development, testing, and production
- **Faster deployment** with pre-built dependencies
- **Resource efficiency** by sharing the host operating system
- **Portability** across different computing environments

---

## Core Services

### GitOps Deployment

CIRRUS uses **GitOps** for application deployment and management:

1. **Code repositories** store application configurations as Helm charts
2. **Argo CD** monitors repositories and automatically deploys changes
3. **Version control** provides audit trails and rollback capabilities
4. **Collaborative workflows** enable team-based development

For deployment guidance, see [Adding Applications](../03-deploying-applications/additions.md).

### Container Registry (Harbor)

**Harbor** provides secure, high-performance container image storage:

- **Local hosting** reduces network latency and increases transfer speeds
- **Vulnerability scanning** identifies security issues in container images
- **Access control** manages who can push and pull images
- **Web interface** available at https://hub.k8s.ucar.edu

Learn more: [Container Registry](../04-container-registry/index.md)

### Secrets Management (OpenBao)

**OpenBao** securely stores sensitive data like API keys and credentials:

- **Encrypted storage** protects secrets at rest
- **Secure injection** into applications via External Secrets Operator
- **UCAR authentication** using CIT credentials
- **Web interface** available at https://bao.k8s.ucar.edu

Learn more: [Secret Manager](../07-secret-manager/openbao.md)

### GitHub Actions Integration

**GitHub Actions runners** enable automated CI/CD workflows:

- **On-demand scaling** provisions runners as needed
- **Secure execution** in isolated environments
- **Direct integration** with CIRRUS services
- **Container builds** using remote BuildKit

Learn more: [GitHub Actions](../05-github-actions/scale-sets.md)

### JupyterHub Environment

**JupyterHub** provides interactive computing capabilities:

- **GPU support** with NVIDIA A2 and A10 Tensor Core GPUs
- **GLADE integration** for direct access to research datasets
- **Dask Gateway** for distributed computing workflows
- **Custom environments** via Binder for reproducible research

Learn more: [Jupyter on CIRRUS](../06-jupyter-on-cirrus/jupyterhub.md)

---

## Hardware Resources

CIRRUS operates on **18 high-performance nodes** providing substantial computing power:

### Compute Specifications

| Resource Type | Quantity | Total Capacity |
|---------------|----------|----------------|
| **CPU Cores** | 832 cores | AMD EPYC 9354P + Intel Xeon Gold 6326 |
| **Memory** | 9.2 TB | 512 GB per node |
| **GPU Nodes** | 10 nodes | 5× NVIDIA A10, 5× NVIDIA A2 |
| **Storage** | 246.4 TB | High-speed NVMe across all nodes |
| **Network** | 25G/10G | High-bandwidth interconnect |

### Infrastructure Status

**Operational** (v1-beta production release)

---

## Getting Started

Ready to deploy on CIRRUS? Here's your path forward:

1. **Review** the [Service Level Agreements](../08-service-level-agreements/slas.md)
2. **Containerize** your application using our [containerization guide](../03-deploying-applications/containerize.md)
3. **Submit** a deployment request via our [team interaction process](../02-interact-with-cirrus-team/create-tickets.md)
4. **Deploy** using our GitOps workflow with Helm charts

Need help? The CIRRUS team is here to assist with onboarding, troubleshooting, and optimization.