# Create Dockerfile (1/2): the Build phase

First create an empty Dockerfile:

`touch /root/mfpconnector/Dockerfile`{{execute}}

than open it in the editor (/root/mfpconnector) and insert the following:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="replace">
#-------------------------------------------------
# BUILD STAGE
#-------------------------------------------------
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-bionic AS build
ARG app_version="0.1.0"
</pre>

Than you can copy all source code file inside the Docker image you are creating:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="append">
# Beware!!! This will copy everything!
COPY . ./
</pre>

Setup the correct working directory:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="append">
WORKDIR /MFPConnector/
</pre>

Resolve dependencies:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="append">
# Resolve dependencies
RUN dotnet restore \
    MFPConnector.sln \
    -r ubuntu.18.04-x64 \
    -s https://nexus.kmiservicehub.com/repository/NuGet/ \
    -s https://api.nuget.org/v3/index.json
</pre>

Finally perform the build:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="append">
# Build MfpCore
RUN dotnet publish ServiceHub.Web.MfpConnector/ServiceHub.Web.MfpConnector.csproj \
    -r ubuntu.18.04-x64 \
    -c Release \
    -f netcoreapp2.2 \
    -o app /p:Version=$app_version
</pre>

In ordert to see some result in our container we add a simple command to see the content of the built directory:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="append">
RUN /MFPConnector/ServiceHub.Web.MfpConnector/app
</pre>

Your Dockerfile is completed: the image you are creating will build MfpCore in a containerized environment!

In order to perform the build you need to invoke:

`docker build -t mfpcore .`{{execute}}

And finally you can run the container:

`docker run mfpcore`{{execute}}

