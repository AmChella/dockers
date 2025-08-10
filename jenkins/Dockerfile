FROM ubuntu:22.04

# Install dependencies
RUN apt-get update && apt-get install -y wget gnupg openjdk-21-jdk

# Add Jenkins repo and key
RUN mkdir -p /etc/apt/keyrings \
    && wget -O /etc/apt/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key \
    && echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" \
       | tee /etc/apt/sources.list.d/jenkins.list > /dev/null

# Install Jenkins
RUN apt-get update && apt-get install -y jenkins

# Expose ports
EXPOSE 8080 50000

# Start Jenkins directly (no systemd)
CMD ["java", "-jar", "/usr/share/java/jenkins.war"]