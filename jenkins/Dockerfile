FROM ubuntu:22.04

# Set environment variables
ENV JENKINS_HOME /var/jenkins_home

# Install Jenkins and dependencies
RUN apt-get update && \
    apt-get install -y openjdk-11-jdk curl gnupg2 && \
    curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | apt-key add - && \
    echo "deb https://pkg.jenkins.io/debian binary/" > /etc/apt/sources.list.d/jenkins.list && \
    apt-get update && \
    apt-get install -y jenkins && \
    apt-get clean

# Create Jenkins home directory
RUN mkdir -p /var/jenkins_home && chown -R jenkins:jenkins /var/jenkins_home

# Expose Jenkins port
EXPOSE 8080

# Start Jenkins
CMD ["java", "-jar", "/usr/share/jenkins/jenkins.war"]
