# CAR Server

CAR’s cloud server manages centralizing operations, synchronizing annotation data, and resolving any conflicts that may arise.

## Installation

The software can be run using two methods and listens to port 8000 by default. If the software does not work properly, please check your firewall configuration first.

### Run from Releases

The server is released as a container image, including all required dependencies. You can run it in linux system using a container management tool, such as [docker](https://www.docker.com/) or [podman](https://podman.io/).

Run server with docker:

```sh
docker start braintellserver && \
    docker exec braintellserver /bin/bash -c "nohup /home/BrainTellServer/BrainTellServer0626 &."
```

### Run from Source Code

The server is written in [go language](https://go.dev/), please install the tool chain. The entry file is placed in the project root directory, try clone the repository and run it in debug mode with `go run .`. You can also use `go build .` to compile a binary release.

## Test Server

To facilitate you to test CAR, we provide a test server. Please note that for security and cost reasons, the test server DOES NOT provide any Server-Level Protocols (SLA) and should not be used in production environments.

The test server information is as follows:

- **Test Server IP**: 114.117.165.134
- **Test Server Port**: 26000
- **Test Account 1**:
    - **Username**: testuser
    - **Password**: 123456
- **Test Account 2**:
    - **Username**: testuser02
    - **Password**: 123456
