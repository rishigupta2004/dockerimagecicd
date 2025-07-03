# Docker CI/CD Pipeline with Flask and GitHub Actions

## 🚀 Overview

This repository demonstrates a complete CI/CD pipeline implementation using GitHub Actions, Docker, and Flask. The project showcases automated workflow orchestration that builds, tests, and deploys a Flask application using Docker containers, with seamless integration to Docker Hub for image distribution.

## 📋 Table of Contents

- [Features](#features)
- [Architecture](#architecture)
- [Prerequisites](#prerequisites)
- [Quick Start](#quick-start)
- [CI/CD Pipeline](#cicd-pipeline)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

- **Automated CI/CD Pipeline**: Complete workflow automation using GitHub Actions
- **Flask Web Application**: Lightweight Python web framework implementation
- **Docker Integration**: Containerized application for consistent deployment
- **Docker Hub Publishing**: Automated image publishing to Docker Hub registry
- **Multi-stage Builds**: Optimized Docker images for production
- **Environment Management**: Configurable environments for different deployment stages

## 🏗️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   GitHub Repo   │───▶│  GitHub Actions │───▶│   Docker Hub    │
│                 │    │                 │    │                 │
│ • Flask App     │    │ • Build         │    │ • Image Store   │
│ • Dockerfile    │    │ • Test          │    │ • Version Tags  │
│ • Workflow      │    │ • Deploy        │    │ • Distribution  │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## 🔧 Prerequisites

Before getting started, ensure you have the following installed:

- [Docker](https://www.docker.com/get-started) (v20.10+)
- [Docker Compose](https://docs.docker.com/compose/install/) (v2.0+)
- [Git](https://git-scm.com/downloads)
- [Python](https://www.python.org/downloads/) (v3.8+)

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/rishigupta2004/dockerimagecicd.git
cd dockerimagecicd
```

### 2. Local Development Setup

```bash
# Install dependencies
pip install -r requirements.txt

# Run the Flask application locally
python app.py
```

The application will be available at `http://localhost:5000`

### 3. Docker Setup

```bash
# Build the Docker image
docker build -t flask-cicd-app .

# Run the container
docker run -p 5000:5000 flask-cicd-app
```

## 🔄 CI/CD Pipeline

The GitHub Actions workflow automatically triggers on:

- **Push to main branch**: Full CI/CD pipeline execution
- **Pull requests**: Build and test validation
- **Manual trigger**: On-demand pipeline execution

### Pipeline Stages

1. **Code Checkout**: Retrieves the latest code from the repository
2. **Environment Setup**: Configures Python and Docker environments
3. **Dependency Installation**: Installs required packages
4. **Testing**: Runs unit tests and code quality checks
5. **Docker Build**: Creates optimized Docker images
6. **Image Tagging**: Applies version tags and latest tag
7. **Docker Hub Push**: Publishes images to Docker Hub registry
8. **Deployment**: Deploys to target environment (if configured)

## 📁 Project Structure

```
dockerimagecicd/
├── .github/
│   └── workflows/
│       └── ci-cd.yml          # GitHub Actions workflow
├── app/
│   ├── __init__.py
│   ├── app.py                 # Flask application
│   ├── requirements.txt       # Python dependencies
│   └── templates/
│       └── index.html         # HTML templates
├── tests/
│   └── test_app.py            # Unit tests
├── Dockerfile                 # Docker configuration
├── docker-compose.yml         # Docker Compose setup
├── .dockerignore              # Docker ignore file
└── README.md                  # Project documentation
```

## ⚙️ Configuration

### Environment Variables

Create a `.env` file in the root directory:

```env
# Flask Configuration
FLASK_ENV=production
FLASK_DEBUG=False
SECRET_KEY=your-secret-key-here

# Docker Hub Configuration
DOCKER_USERNAME=your-dockerhub-username
DOCKER_PASSWORD=your-dockerhub-password
```

### GitHub Secrets

Configure the following secrets in your GitHub repository:

- `DOCKER_USERNAME`: Your Docker Hub username
- `DOCKER_PASSWORD`: Your Docker Hub password or access token

## 🚢 Deployment

### Docker Hub Image

Pull and run the latest image:

```bash
docker pull rishigupta2004/flask-cicd-app:latest
docker run -p 5000:5000 rishigupta2004/flask-cicd-app:latest
```

### Docker Compose

For production deployment:

```bash
docker-compose up -d
```

## 🧪 Testing

Run the test suite:

```bash
# Unit tests
python -m pytest tests/

# With coverage
python -m pytest tests/ --cov=app --cov-report=html
```

## 🔍 Monitoring and Logging

The application includes:

- Health check endpoints
- Structured logging
- Docker container monitoring
- CI/CD pipeline status tracking

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Flask community for the excellent web framework
- Docker for containerization technology
- GitHub Actions for CI/CD automation
- Contributors and maintainers

---

**Made with ❤️ by [Rishi Gupta](https://github.com/rishigupta2004)**
