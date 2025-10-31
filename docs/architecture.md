# System Architecture (Unified Edition)

## Overview
DevOps Simulator adopts a **microservices-based architecture** emphasizing **high availability**, **scalability**, and **modular design**.  
It operates efficiently across both **Production** and **Development** environments, while also supporting **AI-powered experimental extensions** for predictive scaling and anomaly detection.

---

## 🧩 Core Components

### 1. Application Server
| Environment | Configuration |
|--------------|----------------|
| **Technology** | Node.js + Express *(TensorFlow.js in experimental mode)* |
| **Production** | Port: `8080` • Horizontal auto-scaling (Kubernetes) |
| **Development** | Port: `3000` • Hot reload + Chrome DevTools on port `9229` |
| **Experimental (AI Mode)** | Ports: `9000` (main), `9001` (metrics), `9002` (AI API) • Predictive auto-scaling via ML models |

**Notes:**
- AI-enabled builds use **TensorFlow.js** for inference and **Kafka** for event streaming.
- Rolling updates ensure zero-downtime deployments.

---

### 2. Database Layer
| Environment | Configuration |
|--------------|----------------|
| **Production** | PostgreSQL 14 with master-slave replication, daily backups, SSL enabled |
| **Development** | Local PostgreSQL instance, seeded test data, manual backups |
| **Experimental** | Multi-master PostgreSQL cluster (5 nodes) • Redis cache with ML-based optimization • Geo-redundant continuous backup |

**AI Features (Experimental):**
- Smart index suggestions  
- Query pattern optimization  

---

### 3. Monitoring System
| Environment | Configuration |
|--------------|----------------|
| **Production** | Prometheus + Grafana • Alerts via email for critical issues |
| **Development** | Console logs with Prometheus optional • Build time metrics |
| **Experimental** | Prometheus + Thanos (for long-term storage) • ELK Stack with AI-powered log analysis • Predictive anomaly alerts |

---

### 4. Container & Orchestration Layer
| Environment | Tooling |
|--------------|----------|
| **Development** | Docker Compose (App + DB + Redis) with volume mounts and live reloading |
| **Production** | Kubernetes (Rolling updates, Auto-healing) |
| **Experimental** | Multi-cloud orchestration via Kubernetes Custom Resource Definitions (CRDs) • Cross-cloud failover • Global Anycast GeoDNS |

---

### 5. Authentication System
| Environment | Method |
|--------------|---------|
| **Development** | OAuth2 + JWT • Providers: Google, GitHub • Redis session storage |
| **Production** | Secure OAuth2 + Encrypted session management |
| **Experimental** | AI-based risk scoring and adaptive authentication (in testing) |

---

## 🚀 Deployment Strategy
| Environment | Deployment Type | Rollback |
|--------------|----------------|-----------|
| **Production** | Rolling updates • Zero downtime ✅ | Automated rollback on failure |
| **Development** | Docker Compose hot reload | Git revert / commit rollback |
| **Experimental** | AI-guided predictive deployment (testing phase) | Anomaly-triggered rollback |

---

## 🧪 Experimental AI/ML Pipeline (Beta)
| Feature | Description |
|----------|-------------|
| **Frameworks** | TensorFlow, PyTorch, Scikit-learn |
| **Models** | LSTM (Anomaly detection), XGBoost (Load prediction), Reinforcement Learning (Auto-scaling) |
| **Training** | Continuous online learning |
| **Inference** | <50ms latency predictions |
| **Goal** | Proactive system scaling & fault prevention |

---

## 🛡️ Security
| Environment | Measures |
|--------------|-----------|
| **Production** | SSL/TLS encryption • Encrypted DB connections • Regular audits |
| **Development** | SSL disabled (local only) • CORS enabled • Debug endpoints exposed |
| **Experimental** | Federated identity with ML-based risk evaluation (under review) |

---

## 🧰 Development Workflow
1. Modify source code  
2. Hot reload triggers rebuild  
3. Run unit tests (`npm test`)  
4. Check logs for warnings/errors  
5. Commit and push verified changes  

---

## ⚙️ Experimental Features (Testing Phase)
🚧 These are under active development:
- Multi-cloud deployment orchestration  
- AI-powered log & anomaly analysis  
- Automatic rollback via anomaly detection  
- Predictive scaling based on workload trends  

---

✅ **Final Status:**  
All merge conflicts have been successfully resolved.  
The document now integrates **stable (production/dev)** configurations with **experimental AI/ML architecture** while avoiding redundancy and maintaining clarity.
