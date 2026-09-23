# 🚀 DevOps CI/CD Project

A simple **DevOps CI/CD project** demonstrating automated testing and deployment of an HTML application from **GitLab to AWS EC2 using Docker and Nginx**.

## 🏗️ Architecture

```text
Developer
   ↓
GitLab Repository
   ↓
GitLab CI/CD Pipeline
   ↓
Test Job
   ↓
Deploy Job
   ↓
SSH → AWS EC2
   ↓
Docker Build
   ↓
Docker Container
   ↓
Nginx
   ↓
🌐 Web Application
```

## 🛠️ Technologies Used

- Git & GitLab
- GitLab CI/CD
- YAML
- Docker
- Nginx
- AWS EC2
- SSH
- Linux / Ubuntu
- HTML

## 📁 Project Structure

```text
devops-cicd-project/
├── index.html
├── Dockerfile
├── .gitlab-ci.yml
└── README.md
```

## 🔄 CI/CD Workflow

1. Push code to GitLab.
2. GitLab automatically starts the CI/CD pipeline.
3. The **test** job checks that `index.html` and `Dockerfile` exist.
4. The **deploy** job connects to the AWS EC2 instance using SSH.
5. Application files are copied to EC2.
6. Docker builds the application image.
7. The previous container is removed if it exists.
8. A new Docker container is started on port `80`.
9. Nginx serves the application through the EC2 public IP.

## 🐳 Dockerfile

```dockerfile
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

## ⚙️ GitLab CI/CD

The pipeline uses two stages:

```yaml
stages:
  - test
  - deploy
```

### Test Stage

```bash
test -f index.html
test -f Dockerfile
```

### Deploy Stage

The deploy job installs the SSH client, creates the SSH key file, connects to EC2, copies the application files, builds the Docker image, and starts the container.

## 🔐 CI/CD Variables

Configure these variables in **GitLab → Settings → CI/CD → Variables**:

| Variable | Purpose |
|---|---|
| `EC2_HOST` | EC2 public IP address |
| `EC2_USER` | EC2 SSH username (`ubuntu`) |
| `EC2_SSH_KEY` | SSH private key used by the pipeline |

> **Security:** Never commit a private SSH key to the repository. Store it as a protected/masked CI/CD variable.


## 🌐 Deployment

The application is deployed on an **AWS EC2 instance** and served through Docker/Nginx on port `80`.

```text
http://<EC2-PUBLIC-IP>
```

## 🎯 Learning Outcomes

- GitLab CI/CD pipeline creation
- Writing `.gitlab-ci.yml`
- CI/CD variables and SSH authentication
- Docker image building and container deployment
- Nginx web server configuration
- AWS EC2 deployment
- Automated application delivery

## 👨‍💻 Author

**Kiran Kumbhar**  
BE – Artificial Intelligence & Data Science  
Savitribai Phule Pune University (SPPU), Pune

---

⭐ **GitLab → CI/CD → Docker → AWS EC2**
