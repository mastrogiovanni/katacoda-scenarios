Welcome to the step-by-step guide for the migration of MfpCore!

In this tutorial (not intended to be exaustive) we will approach migration of this component under three main aspects:

 # Hello

 - one
 - two
 - three

  Hello World

`git clone https://bitbucket.kmiservicehub.com/scm/sh/mfpconnector.git`{{execute}}

`https://bitbucket.kmiservicehub.com/scm/sh/mfpservice.git`{{execute}}

`
curl -Lo ./kind https://github.com/kubernetes-sigs/kind/releases/download/v0.5.1/kind-$(uname)-amd64
chmod +x ./kind
mv ./kind /some-dir-in-your-PATH/kind
`{{execute}}

<pre class="file" data-filename="Dockerfile" data-target="replace" data-katacoda-layout="editor-terminal-split">var http = require('http');
var requestListener = function (req, res) {
  res.writeHead(200);
  res.end('Hello, World!');
}

var server = http.createServer(requestListener);
server.listen(3000, function() { console.log("Listening on port 3000")});
</pre>
          


<pre class="file" data-target="clipboard">Test</pre>
          


<pre class="file" data-target="regex???">Test</pre>
          



