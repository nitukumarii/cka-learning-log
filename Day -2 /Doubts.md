# Docker Confusing Points (Quick Notes)

## 1. Image vs Container

Image = blueprint
Container = running instance

docker run nginx

---

## 2. Why containers stop

Container runs only while main process is running

docker run busybox echo "Hello"

---

## 3. RUN vs CMD

RUN = build time (creates layer)
CMD = runtime (default command)

---

## 4. Tag vs Image Name

docker build -t my-app .
docker tag my-app username/my-app:v1

---

## 5. latest tag issue

docker pull nginx

# actually pulls nginx:latest

Better:
docker pull nginx:1.25

---

## 6. docker ps vs docker ps -a

docker ps      # running only
docker ps -a   # all containers

---

## 7. Container name auto-generated

docker run --name my-container nginx

---

## 8. Push requires login

docker login
docker push username/image

---

## 9. Cannot remove image

docker rm <container_id>
docker rmi <image>

---

## 10. Core flow

Dockerfile → Image → Container
