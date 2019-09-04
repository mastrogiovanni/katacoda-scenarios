# Create Dockerfile (1): the Build phase

First create an empty Dockerfile from the terminal:

`touch Dockerfile`{{execute}}

Open the Dockerfile in the editor and copy inside:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="insert">
#-------------------------------------------------
# BUILD STAGE
#-------------------------------------------------
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-bionic AS build
ARG app_version="0.1.0"
</pre>

Than you can copy all source code file inside the Docker image you are creating:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="insert">
# Beware!!! This will copy everything!
COPY . ./
</pre>

Setup the correct working directory:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="insert">
WORKDIR /MFPConnector/
</pre>

Resolve dependencies:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="insert">
# Setup dependencies
RUN dotnet restore \
    MFPConnector.sln \
    -r ubuntu.18.04-x64 \
    -s https://nexus.kmiservicehub.com/repository/NuGet/ \
    -s https://api.nuget.org/v3/index.json
</pre>

Finally perform the build:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="insert">
# Build MfpCore
RUN dotnet publish ServiceHub.Web.MfpConnector/ServiceHub.Web.MfpConnector.csproj \
    -r ubuntu.18.04-x64 \
    -c Release \
    -f netcoreapp2.2 \
    -o app /p:Version=$app_version
</pre>

In ordert to see some result in our container we add a simple command to see the content of the built directory:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="insert">
RUN /MFPConnector/ServiceHub.Web.MfpConnector/app
</pre>

