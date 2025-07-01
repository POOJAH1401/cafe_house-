# ☕ Cafe House - CI/CD Static Website Deployment

This project showcases the deployment of a static HTML/CSS/JS website using a complete CI/CD pipeline built with Jenkins, Docker, GitHub, and AWS EC2.

---

## 🧰 Tech Stack & Tools

- **Jenkins** – Continuous Integration & Deployment
- **Docker** – Containerization of static website
- **DockerHub** – Hosting the Docker image
- **GitHub** – Source code version control
- **AWS EC2 (Ubuntu)** – Hosting Jenkins and Docker container
- **GitHub Webhooks** – Trigger Jenkins builds on code push

---


---

## 🛠️ CI/CD Pipeline Flow

1. **Push to GitHub**  
   Code is updated in the GitHub repository.

2. **Webhook Trigger**  
   GitHub Webhook notifies Jenkins of the new change.

3. **Jenkins Pipeline**  
   - Clones the code from GitHub  
   - Builds Docker image using the Dockerfile  
   - Pushes image to DockerHub  
   - Pulls and runs the image on the EC2 instance

4. **Website Live**  
   The website is accessible via public IP on port 80.

---


## 🛠️ CI/CD Pipeline Flow

1. **Push to GitHub**  
   Code is updated in the GitHub repository.

2. **Webhook Trigger**  
   GitHub Webhook notifies Jenkins of the new change.

3. **Jenkins Pipeline**  
   - Clones the code from GitHub  
   - Builds Docker image using the Dockerfile  
   - Pushes image to DockerHub  
   - Pulls and runs the image on the EC2 instance

4. **Website Live**  
   The website is accessible via public IP on port 80.

---

---

## 🐳 Docker Commands (Optional Use)

```bash
# Build Docker image locally
docker build -t cafe-house .

# Tag and push to DockerHub
docker tag cafe-house pooja1415/cafe-house:latest
docker push pooja1415/cafe-house:latest

# Run the container on EC2
docker run -d --name cafe-house -p 80:80 pooja1415/cafe-house:latest
