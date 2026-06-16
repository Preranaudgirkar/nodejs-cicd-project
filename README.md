
# Node.js CI/CD Pipeline with Jenkins

## Project Overview

This project demonstrates a complete Continuous Integration and Continuous Deployment (CI/CD) pipeline for a Node.js application using Jenkins, GitHub, and PM2.

The pipeline automatically performs source code retrieval, dependency installation, and application deployment whenever changes are pushed to the GitHub repository.

---

## Technology Stack

* Node.js
* Express.js
* Jenkins
* Git & GitHub
* PM2
* Ubuntu Server
* AWS EC2

---

## Project Structure

```text
.
├── app.js
├── package.json
├── package-lock.json
├── Jenkinsfile
├── README.md
└── .gitignore
```

---

## CI/CD Workflow

```text
Developer
    |
    | Git Push
    v
GitHub Repository
    |
    | Webhook Trigger
    v
Jenkins Pipeline
    |
    +--> Clone Repository
    |
    +--> Install Dependencies
    |
    +--> Build / Verify Application
    |
    +--> Deploy Application using PM2
    |
    v
Production Server
```

---

## Jenkins Pipeline Jobs

### 01 - Git Clone

Purpose:

* Clone source code from GitHub repository
* Pull latest changes from the configured branch

### 02 - Dependency Installation

Purpose:

* Install project dependencies

Command:

```bash
npm install
```

### 03 - Application Deployment

Purpose:

* Deploy and manage application using PM2

Commands:

```bash
pm2 delete nodeapp || true
pm2 start app.js --name nodeapp
pm2 save
```

---

## Installation

### Clone Repository

```bash
git clone https://github.com/<username>/<repository-name>.git
cd <repository-name>
```

### Install Dependencies

```bash
npm install
```

### Run Application

```bash
node app.js
```

---

## PM2 Process Management

### Install PM2

```bash
npm install -g pm2
```

### Start Application

```bash
pm2 start app.js --name nodeapp
```

### Check Status

```bash
pm2 status
```

### View Logs

```bash
pm2 logs nodeapp
```

### Stop Application

```bash
pm2 stop nodeapp
```

### Restart Application

```bash
pm2 restart nodeapp
```

---

## Jenkins Configuration

### Required Plugins

* Git Plugin
* Git Client Plugin
* Credentials Plugin
* Credentials Binding Plugin
* SSH Credentials Plugin
* Pipeline Plugin
* GitHub Plugin

### Build Triggers

Enable:

```text
GitHub hook trigger for GITScm polling
```

---

## GitHub Webhook Configuration

Navigate to:

```text
GitHub Repository
→ Settings
→ Webhooks
→ Add Webhook
```

Payload URL:

```text
http://<jenkins-server-ip>:8080/github-webhook/
```

Content Type:

```text
application/json
```

Events:

```text
Just the push event
```

---

## Environment Requirements

| Component | Version    |
| --------- | ---------- |
| Node.js   | 18+        |
| npm       | 9+         |
| Jenkins   | Latest LTS |
| PM2       | Latest     |
| Ubuntu    | 22.04 LTS  |

---

## Verification

Verify application status:

```bash
pm2 status
```

Verify Jenkins service:

```bash
sudo systemctl status jenkins
```

Verify Git installation:

```bash
git --version
```

---

## Future Improvements

* Docker Containerization
* Kubernetes Deployment
* SonarQube Code Quality Analysis
* Automated Testing
* AWS CodeDeploy Integration
* Infrastructure as Code using Terraform

---

## Author

Prerana Udgirkar

## License

This project is licensed under the MIT License.
