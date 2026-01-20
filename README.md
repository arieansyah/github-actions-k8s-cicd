# 🚀 Kubernetes Modern Deployment Pipeline

<div align="center">

[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![Helm](https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white)](https://helm.sh/)
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)](https://github.com/features/actions)
[![Vault](https://img.shields.io/badge/Vault-CA2171?style=for-the-badge&logo=vault&logoColor=white)](https://www.vaultproject.io/)

<p align="center">
  <strong>Enterprise-grade CI/CD pipeline for Kubernetes with automated Semantic Versioning, Helm Packaging, and Vault Integrations.</strong>
</p>

[Explore Documentation](docs/GITHUB_WORKFLOWS.md) • [Report Bug](https://github.com/org/repo/issues) • [Request Feature](https://github.com/org/repo/issues)

</div>

---

## 📖 Overview

Project ini menyediakan template infrastruktur lengkap untuk men-deploy aplikasi containerized ke Kubernetes. Dirancang dengan prinsip **GitOps**, pipeline ini menangani seluruh siklus rilis mulai dari Pull Request hingga Production deployment dengan standar keamanan tinggi.

### ✨ Key Features

- **🔄 Automated Versioning**: Versi rilis (`v1.2.0`) dihitung otomatis berdasarkan label PR (`[major]`, `[minor]`, `[patch]`).
- **📦 Helm Chart Management**: Packaging dan distribusi aplikasi menggunakan OCI Registry standar.
- **🔐 Secret Injection**: Integrasi seamless dengan HashiCorp Vault untuk manajemen credentials yang aman (No more base64 secrets!).
- **🌍 Multi-Environment**: Workflow terpisah untuk `Development`, `Staging`, dan `Production` dengan isolasi penuh.
- **🛡️ Secure Runners**: Menggunakan Self-Hosted Runners yang dikelompokkan per environment.

---

## 🛠️ Technology Stack

| Component         | Technology                                                                                        | Description                      |
| ----------------- | ------------------------------------------------------------------------------------------------- | -------------------------------- |
| **Orchestration** | ![K8s](https://img.shields.io/badge/-Kubernetes-326CE5?logo=kubernetes&logoColor=white)           | Container orchestration platform |
| **Packaging**     | ![Helm](https://img.shields.io/badge/-Helm-0F1689?logo=helm&logoColor=white)                      | Package manager for Kubernetes   |
| **CI/CD**         | ![GHA](https://img.shields.io/badge/-GitHub%20Actions-2088FF?logo=github-actions&logoColor=white) | Automation workflows             |
| **Secrets**       | ![Vault](https://img.shields.io/badge/-Vault-CA2171?logo=vault&logoColor=white)                   | Secrets management & injection   |
| **Registry**      | ![Docker](https://img.shields.io/badge/-Docker%20Registry-2496ED?logo=docker&logoColor=white)     | Container & Chart storage        |

---

## 📂 Project Structure

```bash
.
├── .github/workflows/    # CI/CD Pipeline definitions
│   ├── dev.yaml          # Development workflow
│   ├── staging.yaml      # Staging workflow
│   └── production.yaml   # Production workflow
├── helm/                 # Helm Chart Configuration
│   ├── templates/        # K8s manifests (Deployment, Service, etc.)
│   ├── values.yaml       # Default configuration
│   └── [env].yaml        # Environment specific overrides
└── docs/                 # Detailed documentation
```

---

## 🚀 Getting Started

### Prerequisites

- Kubernetes Cluster v1.25+
- Helm v3.x
- HashiCorp Vault (optional, for secret injection)
- Docker Registry

### Installation

1. **Clone Repository**

   ```bash
   git clone https://github.com/your-org/my-k8s-project.git
   cd my-k8s-project
   ```

2. **Setup Secrets**
   Pastikan Repository Secrets berikut telah dikonfigurasi:
   - `KUBE_CONFIG`
   - `REGISTRY_USERNAME`
   - `REGISTRY_PASSWORD`

3. **Deploy Manually (Local Testing)**
   ```bash
   helm upgrade --install my-app ./helm \
     --values ./helm/dev.yaml \
     --namespace my-namespace
   ```

---

## 🔄 Deployment Flow

Tiap environment memiliki strategi deployment unik:

| Env             | Trigger             | Versioning | Deployment Goal     |
| --------------- | ------------------- | ---------- | ------------------- |
| **Development** | PR merged to `dev`  | `*-alpha`  | Feature testing     |
| **Staging**     | PR merged to `stg`  | `*-beta`   | Integration testing |
| **Production**  | PR merged to `main` | `vX.Y.Z`   | Stable Release      |

👉 **Baca dokumentasi detail:** [GITHUB_WORKFLOWS.md](docs/GITHUB_WORKFLOWS.md)

---

## 🤝 Contributing

1. Fork project ini
2. Create Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit Changes (`git commit -m '[minor] Add some AmazingFeature'`) - _Perhatikan prefix `[minor]`!_
4. Push ke Branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

---

<div align="center">
  <sub>Built with ❤️ by Arieansyah</sub>
</div>
