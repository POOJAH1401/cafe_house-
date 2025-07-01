☕ Cafe House - CI/CD Static Website Deployment
This project showcases the deployment of a static HTML/CSS/JS website using a complete CI/CD pipeline built with Jenkins, Docker, GitHub, and AWS EC2.

🧰 Tech Stack & Tools

Jenkins – Continuous Integration & Deployment
Docker – Containerization of static website
DockerHub – Hosting the Docker image
GitHub – Source code version control
AWS EC2 (Ubuntu) – Hosting Jenkins and Docker container
GitHub Webhooks – Trigger Jenkins builds on code push


🔄 CI/CD Pipeline Flow

Push to GitHub
Code is updated in the GitHub repository.
Webhook Trigger
GitHub Webhook notifies Jenkins of the new change.
Jenkins Pipeline

Clones the code from GitHub
Builds Docker image using the Dockerfile
Pushes image to DockerHub
Pulls and runs the image on the EC2 instance


Website Live
The website is accessible via public IP on port 80.


🛠️ Quick Setup
Prerequisites

AWS EC2 instance (t2.medium, Ubuntu 20.04+)
GitHub, DockerHub accounts
Security group: ports 22 (SSH), 80 (HTTP), 8080 (Jenkins)

Installation Commands
# Install Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER

# Install Jenkins
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update && sudo apt install jenkins -y
sudo systemctl start jenkins && sudo systemctl enable jenkins

GitHub Webhook Setup
Repository → Settings → Webhooks
URL: http://<ec2-ip>:8080/github-webhook/
Content type: application/json


🐳 Docker Commands
# Build Docker image locally
docker build -t cafe-house .

# Tag and push to DockerHub
docker tag cafe-house pooja1415/cafe-house:latest
docker push pooja1415/cafe-house:latest

# Run the container on EC2
docker run -d --name cafe-house -p 80:80 pooja1415/cafe-house:latest

🔧 Jenkins Access

URL: http://<ec2-ip>:8080
Initial password: sudo cat /var/lib/jenkins/secrets/initialAdminPassword


⭐ Star this repository if you found it helpful!
