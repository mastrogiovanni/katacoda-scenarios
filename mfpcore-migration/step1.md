Welcome to the step-by-step guide for the migration of MfpCore!

In this tutorial (not intended to be exaustive) we will approach migration of this component under three main aspects:

# Welcome!

In the first part of this tutorial we want to create a Docker image around the MfpCore component.

First, start downloading the bitbucket code:

`git clone https://bitbucket.kmiservicehub.com/scm/sh/mfpconnector.git`{{execute}}

Enter your Bitbucket credential in order to download the source code.

After download the code, enter in the projects's directory:

`cd mfpconnector`{{execute}}

`
curl -Lo ./kind https://github.com/kubernetes-sigs/kind/releases/download/v0.5.1/kind-$(uname)-amd64
chmod +x ./kind
mv ./kind /some-dir-in-your-PATH/kind
`{{execute}}

<pre class="file" data-filename="/root/Dockerfile" data-target="insert">var http = require('http');
var requestListener = function (req, res) {
  res.writeHead(200);
  res.end('Hello, World!');
}

var server = http.createServer(requestListener);
server.listen(3000, function() { console.log("Listening on port 3000")});
</pre>
          


<pre class="file" data-target="clipboard">Test</pre>
          


<pre class="file" data-target="regex???">Test</pre>
          



