# Jenkins on Ubuntu Docker Image

A Docker image that installs Jenkins on top of Ubuntu 22.04, with OpenJDK 11, exposing port 8080.

## 🚀 Features

- **Base Image:** Ubuntu 22.04
- **Jenkins:** Installed from official Jenkins APT repository
- **Java:** OpenJDK 11
- **Port:** 8080 exposed for Jenkins UI

## 🧰 How to Use

### Build Image

```bash
docker build -t my-jenkins .
```

### Run Container

```bash
docker run -d -p 8080:8080 --name jenkins-server my-jenkins
```

Then, visit: [http://localhost:8080](http://localhost:8080)

### Get Initial Admin Password

```bash
docker exec jenkins-server cat /var/jenkins_home/secrets/initialAdminPassword
```

## 📁 Jenkins Home

- Jenkins stores all configuration in: `/var/jenkins_home`
- You can mount a volume to persist data:

```bash
docker run -d -p 8080:8080 -v jenkins_data:/var/jenkins_home --name jenkins-server my-jenkins
```

## 📦 Exposed Ports

- `8080`: Jenkins Web Interface

## 🛠️ Default Command

```bash
java -jar /usr/share/jenkins/jenkins.war
```
