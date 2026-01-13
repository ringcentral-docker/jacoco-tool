# JaCoCo Tool Docker Image

A Docker image that provides JaCoCo CLI and Swagger Coverage tools for Java code coverage analysis and API testing.

## Overview

This Docker image is built on top of `ringcentral/jdk:17-noble` and includes:

- **JaCoCo CLI**: Java Code Coverage Library command-line interface
- **Swagger Coverage**: API coverage analysis tool
- Essential development tools (git, curl, wget, zip, etc.)

## Features

- 🚀 Based on JDK 17 (Ubuntu Noble)
- 📊 Pre-installed JaCoCo CLI for code coverage reporting
- 🔍 Swagger Coverage tool for API testing coverage
- 🛠️ Common development utilities included
- ⚡ Automated builds via GitHub Actions

## Quick Start

### Pull the Image

```bash
docker pull ringcentral/jacoco-tool:latest
```

### Run JaCoCo CLI

```bash
docker run --rm -v $(pwd):/workspace ringcentral/jacoco-tool:latest \
  java -jar /opt/jacoco/jacococli.jar <command> <options>
```

### Run Swagger Coverage

```bash
docker run --rm -v $(pwd):/workspace ringcentral/jacoco-tool:latest \
  swagger-coverage <command> <options>
```

## Usage Examples

### Generate JaCoCo Report

```bash
docker run --rm \
  -v $(pwd):/workspace \
  -w /workspace \
  ringcentral/jacoco-tool:latest \
  java -jar /opt/jacoco/jacococli.jar report jacoco.exec \
  --classfiles ./build/classes \
  --sourcefiles ./src/main/java \
  --html ./coverage-report
```

### Merge JaCoCo Execution Files

```bash
docker run --rm \
  -v $(pwd):/workspace \
  -w /workspace \
  ringcentral/jacoco-tool:latest \
  java -jar /opt/jacoco/jacococli.jar merge *.exec \
  --destfile merged.exec
```

## Included Tools

| Tool             | Location                          | Description             |
| ---------------- | --------------------------------- | ----------------------- |
| JaCoCo CLI       | `/opt/jacoco/jacococli.jar`       | Java code coverage tool |
| Swagger Coverage | `/usr/local/bin/swagger-coverage` | API coverage analysis   |
| Git              | System installed                  | Version control         |
| Maven/Gradle     | Via JDK                           | Build tools support     |

## Image Tags

- `latest`: Latest stable version
- `17-noble`: Specific JDK version tag

## Building Locally

```bash
cd images
docker build -t jacoco-tool:local -f Dockerfile .
```

## CI/CD

This project uses GitHub Actions for automated builds:

- Triggers on pushes to `main` branch
- Automatically builds and pushes to Docker Hub
- Tags images with version from Dockerfile

## Requirements

- Docker 20.10+
- Docker Hub account (for pulling images)

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is open source and available under the MIT License.

## Support

For issues and questions:

- Open an issue on GitHub
- Contact the RingCentral DevOps team

## References

- [JaCoCo Documentation](https://www.jacoco.org/jacoco/trunk/doc/)
- [Swagger Coverage GitHub](https://github.com/xingyu-he/swagger-coverage)
- [Docker Hub Repository](https://hub.docker.com/r/ringcentral/jacoco-tool)

---

**Maintained by**: RingCentral DevOps Team
