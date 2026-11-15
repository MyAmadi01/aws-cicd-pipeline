# aws-cicd-pipeline
Automated CI/CD pipeline using GitHub Actions, Docker and AWS
# Automated AWS CI/CD Pipeline with GitHub Actions, Docker and Amazon ECR

## Project Overview

This project demonstrates an automated CI/CD pipeline that tests, builds, and publishes a containerized Flask application to Amazon Elastic Container Registry (ECR).

The pipeline uses GitHub Actions to automate application testing, Docker image creation, AWS authentication, image publishing, and container health validation.

The goal is to reduce manual deployment tasks and demonstrate a secure, repeatable CI/CD workflow.

## Architecture

**Workflow:**

1. Developer pushes code to GitHub.
2. GitHub Actions triggers the pipeline.
3. Python dependencies are installed.
4. Automated tests run using pytest.
5. Docker builds the application image.
6. GitHub Actions authenticates with AWS using OpenID Connect (OIDC).
7. Docker image is pushed to Amazon ECR.
8. The image is pulled and run in the GitHub Actions runner.
9. The `/health` endpoint is tested.
10. The test container is stopped and removed.

## Technologies Used

- AWS Identity and Access Management (IAM)
- Amazon Elastic Container Registry (ECR)
- GitHub Actions
- Docker
- Python
- Flask
- Pytest
- Git and GitHub
- AWS OIDC authentication

## Application Features

The Flask application provides two endpoints:

| Endpoint | Description |
|---|---|
| `/` | Returns application information and running status |
| `/health` | Returns application health status |

## CI/CD Pipeline Features

- Automated Python testing.
- Docker image building.
- Secure AWS authentication through GitHub OIDC.
- Automated Docker image publishing to ECR.
- Image tagging using Git commit SHA and `latest`.
- Container startup and health-check validation.

## AWS Configuration

**AWS Region:** `us-east-1`

**ECR Repository:** `aws-cicd-pipeline`

**ECR Image URI:**

`695746118696.dkr.ecr.us-east-1.amazonaws.com/aws-cicd-pipeline`

AWS credentials are not stored as permanent access keys in GitHub. GitHub Actions assumes an IAM role through OIDC.

## Running Locally

Clone the repository:

```bash
git clone https://github.com/MyAmadi01/aws-cicd-pipeline.git
cd aws-cicd-pipeline
```

Create a virtual environment and install dependencies:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Run tests:

```bash
python -m pytest -v
```

Build the Docker image:

```bash
docker build -t aws-cicd-pipeline .
```

Run the container:

```bash
docker run -d --name aws-cicd-app -p 5000:5000 aws-cicd-pipeline
```

Test the health endpoint:

```bash
curl http://localhost:5000/health
```

Stop and remove the container:

```bash
docker stop aws-cicd-app
docker rm aws-cicd-app
```

## Project Evidence

Screenshots are available in the `screenshots/` directory, showing:

- Successful GitHub Actions workflow.
- Amazon ECR repository and images.
- AWS IAM OIDC role configuration.
- Successful container health-check validation.

## Security Practices

- GitHub Actions uses OIDC for temporary AWS credentials.
- IAM permissions are restricted to the required ECR repository operations.
- Sensitive credentials are not committed to the repository.
- GitHub Actions permissions follow least-privilege principles.

## Current Project Status

**Completed:**
- Flask application development.
- Automated testing.
- Docker containerization.
- GitHub Actions CI/CD workflow.
- AWS OIDC integration.
- Amazon ECR image publishing.
- Container health-check validation.

**Planned improvements:**
- Deployment to a cloud-hosted environment.
- Infrastructure as Code using Terraform.
- Monitoring and logging.
- Deployment documentation and architecture diagram.

## Author

**Cloud & DevOps Engineering Portfolio Project**

GitHub: https://github.com/MyAmadi01

