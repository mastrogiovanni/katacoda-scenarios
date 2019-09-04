# What is a Dockerfile

In order to create a container for the MfpCore component you need to write a particular receipt: the Dockerfile.

The Dockerfile is a description of how package application binaries in order to create an executable container.

However the Dockerfile allows also the creation of ephemeral containers (multi-stage) that can be used for example to build the source code.

The advantage using Docker to build code is that the build is repeatible in any environment: this simplify the creation and maintenance of CI/CD pipeline.

In our tutorial we show how to create a multi-stage Dockerfilein order to build and create an executable container.
