# System Architecture

## Overview
DevOps Simulator follows a **microservices architecture** designed for **high availability**, **scalability**, and **modular development**.  
It supports both **production** and **development** environments with tailored configurations.

---

## Components

### 1. Application Server
- **Technology**: Node.js + Express  
- **Production**:
  - Port: `8080`
  - Scaling: Horizontal auto-scaling enabled  
  - Deployment: Managed via Kubernetes  
- **Development**:
  - Port: `3000`
  - Hot reload enabled for rapid testing  
  - Chrome DevTools debugger on port `9229`

---

### 2. Database Layer
- **Database**: PostgreSQL 14  
- **Production**:
  - Configuration: Master-slave replication  
  - Backup: Daily automated backups  
  - Security: Encrypted connections  
- **Development**:
  - Configuration: Single local instance  
  - Backup: Manual backups  
  - Seeding: Automatically populated with test data at startup  

---

### 3. Monitoring System
- **Production**:
  - **Tool**: Prometheus + Grafana  
  - **Metrics**: CPU, Memory, Disk, Network  
  - **Alerts**: Email notifications for critical issues  
- **Development**:
  - **Tool**: Console logging (Prometheus optional)  
  - **Metrics**: CPU, Memory, Disk, Network, Build time  
  - **Alerts**: Console warnings only  
  - **Dashboard**: In-development web dashboard  

---

### 4. Container Orchestration (Development Only)
- **Tool**: Docker Compose  
- **Services**:
  - Application Server  
  - Database (PostgreSQL)  
  - Redis Cache  
- **Features**:
  - Volume mounts for live code reloading  
  - Simplified local environment setup  

---

### 5. Authentication System (Beta - Development)
- **Method**: OAuth2 + JWT  
- **Providers**: Google, GitHub (for testing)  
- **Session Management**: Redis-based session storage  

---

## Deployment Strategy
- **Production**:
  - Method: Rolling updates  
  - Zero-downtime: ✅ Yes  
  - Rollback: Automated on failure  
- **Development**:
  - Method: Docker Compose hot reload  
  - Zero-downtime: ❌ Not required (local testing)  
  - Rollback: Git revert or checkout previous commit  

---

## Development Workflow
1. Modify source code  
2. Hot reload rebuilds the app automatically  
3. Run unit tests locally (`npm test`)  
4. Observe console logs for errors or warnings  
5. Commit and push when validated  

---

## Security
- **Production**:
  - SSL/TLS encryption enabled  
  - Database connections encrypted  
  - Regular security audits performed  
- **Development**:
  - SSL/TLS disabled (local only)  
  - Credentials stored in plain text (for testing)  
  - CORS enabled for all origins  
  - Debug endpoints exposed for testing  

---

## Experimental Features (Development Only)
⚠️ These features are currently **under testing** in the dev branch:
- Multi-cloud deployment capabilities  
- AI-powered log analysis system  
- Automatic rollback triggered by anomaly detection  

---

✅ **Final Status**:  
All merge conflicts resolved successfully.  
The document now clearly separates **Production** and **Development** configurations with no redundant or conflicting sections.
