**🧩 1. Docker Setup & Environment**
Install Docker Desktop
Recommended:
Minimum: 4 GB RAM
Ideal: 8–12 GB RAM + 4 CPUs
Alternative if system is weak:
Use cloud VMs like Microsoft Azure or Google Cloud Platform


📦 **2. Docker Hub & Image Basics**
Docker Hub = default public registry
Key concepts:
Registry → storage (Docker Hub)
Repository → collection of images
Image → actual packaged app
Tag → version (e.g., nginx:latest, nginx:1.25)

👉** If no tag is specified → latest is used by default**

⚙️** 3. Core Docker Commands (Must Know)**
🔹 Image Management
docker pull nginx → download image
docker images → list local images
docker rmi nginx → delete image
**🔹 Container Lifecycle
docker run nginx → start container
docker ps → running containers
docker ps -a → all containers**

💡 **Important concept:**

Containers run only while executing a process. Once done → they stop.

Example:

docker run busybox echo "hello docker"

➡ Runs → prints → exits

🔹 Build & Custom Images
docker build -t my-app .

Uses a Dockerfile to create images.

🏗️** 4. Dockerfile Key Concepts**
RUN → creates a new layer
CMD → sets default command (no new layer)

👉 This difference is important for:

Image size
Layer caching
Build performance
🔍 5. Inspection & Debugging
docker history image_name → shows layers
docker inspect container_id → detailed JSON info
📤 6. Tagging & Pushing Images
Step 1: Tag properly
docker tag my-app username/my-app:v1
Step 2: Login
docker login
Step 3: Push
docker push username/my-app:v1

✔ Naming format:

username/repository:tag
🧠 7. Key Takeaways (Exam + Real World)
Docker images = blueprint
Containers = running instances
Images are layered (important for optimization)
Containers are ephemeral (short-lived)
Proper tagging = critical for CI/CD pipelines


Docker Hands-On Lab (Copy-Paste Version)

## Lab 1: Verify Installation

docker --version
docker info

---

## Lab 2: Pull & Manage Images

docker pull nginx
docker images
docker rmi nginx
docker pull nginx

---

## Lab 3: Run Containers

docker run nginx

docker run -d nginx
docker ps
docker ps -a

docker run busybox echo "Hello Docker"

---

## Lab 4: Build Custom Image

mkdir docker-lab
cd docker-lab

# Create Dockerfile

# (create a file named Dockerfile and paste below)

FROM alpine
RUN echo "Building my custom image"
CMD ["echo", "Hello from my Docker image"]

# Build image

docker build -t my-first-image .

# Run image

docker run my-first-image

---

## Lab 5: Inspect Image

docker history my-first-image
docker inspect my-first-image

---

## Lab 6: Tag & Push

docker tag my-first-image yourusername/my-first-image:v1

docker login

docker push yourusername/my-first-image:v1

---

## Lab 7: Cleanup

docker ps -a
docker stop <container_id>
docker rm <container_id>
docker rmi my-first-image

---

## Final Practice

docker pull alpine
docker run alpine echo "CKA Practice"
docker build -t my-image:v2 .
docker tag my-image:v2 yourusername/my-image:v2
docker push yourusername/my-image:v2
