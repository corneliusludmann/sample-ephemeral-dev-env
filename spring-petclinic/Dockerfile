FROM gitpod/openvscode-server:latest

# INSTALL REQUIREMENTS
USER root
RUN apt update && apt install -y \
        default-jdk \
    && rm -rf /var/lib/apt/lists/*


USER openvscode-server

# CLONE REPO
RUN git clone https://github.com/gitpod-io/spring-petclinic.git /home/workspace/project && \
    cd /home/workspace/project && \
    git checkout 68d992e4207faee727434ad682d614af730e2830

# PREBUILD
RUN cd ./project && ./mvnw package -DskipTests

# START APP
# $ java -jar target/*.jar
