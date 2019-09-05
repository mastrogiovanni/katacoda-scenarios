# Create Dockerfile (2/2): the Run phase

Now we will build the final docker image that will contain only binaries that we built in the previous stage:

Add the Dockerfile the following:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="append">
#-------------------------------------------------
# RUN STAGE
#-------------------------------------------------
FROM mcr.microsoft.com/dotnet/core/runtime:2.2-bionic AS run
ARG app_version="0.1.0"
ARG build_date
</pre>

As you noticed the field FROM is different: the build stage needed the .Net SDK and libraries in order to build the code while in the final container you need only the .Net runtime and binaries.

Setup the workdir and copy from the previous image only the compiled application:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="append">
WORKDIR /app/
COPY --from=build /MFPConnector/ServiceHub.Web.MfpConnector/app /app
</pre>

Finally you can setup the main executable for MfpCore:

<pre class="file" data-filename="/root/mfpconnector/Dockerfile" data-target="append">
ENTRYPOINT ["dotnet", "./ServiceHub.Web.MfpConnector.dll"]
</pre>

Launch again the Docker build command in order to create the final running Docker image:

`docker build -t mfpcore .`{{execute}}

And finally you can run the container exposing the port 80 of the container on the 8080 of the machine you are running:

`docker run -p -d 8080:80 mfpcore`{{execute}}

You will see MfpCore logs on console.

You can now check the service with curl


