Welcome to the step-by-step guide for the migration of MfpCore!

In this tutorial (not intended to be exaustive) we will approach migration of this component under three main aspects:

 # Hello

 - one
 - two
 - three

  Hello World

<pre class="file" data-filename="app.js" data-target="replace">var http = require('http');
var requestListener = function (req, res) {
  res.writeHead(200);
  res.end('Hello, World!');
}

var server = http.createServer(requestListener);
server.listen(3000, function() { console.log("Listening on port 3000")});
</pre>
          


<pre class="file" data-target="clipboard">Test</pre>
          


<pre class="file" data-target="regex???">Test</pre>
          



