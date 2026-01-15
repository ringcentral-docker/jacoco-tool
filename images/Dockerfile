FROM ringcentral/jdk:17-noble

RUN apt-get update && apt-get install -y \
    libgcc1 \
    fontconfig \
    fonts-dejavu \
    ca-certificates \
    bash \
    git \
    openssh-client \
    openssl \
    zip \
    subversion \
    sshpass \
    curl \
    wget \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Install swagger-coverage-commandline
ENV SWAGGER_COVERAGE_VERSION=1.1.0
RUN wget https://github.com/xingyu-he/swagger-coverage/releases/download/v1.1.0/swagger-coverage-commandline-1.1.0.zip \
    && unzip swagger-coverage-commandline-1.1.0.zip \
    && mv swagger-coverage-commandline-1.1.0 /opt/swagger-coverage \
    && rm swagger-coverage-commandline-1.1.0.zip \
    && ln -s /opt/swagger-coverage/bin/swagger-coverage-commandline /usr/local/bin/swagger-coverage

# Copy jacococli.jar to the image
COPY jacococli.jar /opt/jacoco/jacococli.jar

#==============
# Show version
#==============
RUN java -version \
    && javac -version