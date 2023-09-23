---
layout:
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: false
  outline:
    visible: false
  pagination:
    visible: false
---

# WEB REQUESTS

### Request Methods

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Method</strong></td><td><strong>Description</strong></td></tr><tr><td><code>GET</code></td><td>Requests a specific resource. Additional data can be passed to the server via query strings in the URL (e.g. <code>?param=value</code>).</td></tr><tr><td><code>POST</code></td><td>Sends data to the server. It can handle multiple types of input, such as text, PDFs, and other forms of binary data. This data is appended in the request body present after the headers. The POST method is commonly used when sending information (e.g. forms/logins) or uploading data to a website, such as images or documents.</td></tr><tr><td><code>HEAD</code></td><td>Requests the headers that would be returned if a GET request was made to the server. It doesn't return the request body and is usually made to check the response length before downloading resources.</td></tr><tr><td><code>PUT</code></td><td>Creates new resources on the server. Allowing this method without proper controls can lead to uploading malicious resources.</td></tr><tr><td><code>DELETE</code></td><td>Deletes an existing resource on the webserver. If not properly secured, can lead to Denial of Service (DoS) by deleting critical files on the web server.</td></tr><tr><td><code>OPTIONS</code></td><td>Returns information about the server, such as the methods accepted by it.</td></tr><tr><td><code>PATCH</code></td><td>Applies partial modifications to the resource at the specified location.</td></tr></tbody></table>

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Code</strong></td><td><strong>Description</strong></td></tr><tr><td><code>200 OK</code></td><td>Returned on a successful request, and the response body usually contains the requested resource.</td></tr><tr><td><code>302 Found</code></td><td>Redirects the client to another URL. For example, redirecting the user to their dashboard after a successful login.</td></tr><tr><td><code>400 Bad Request</code></td><td>Returned on encountering malformed requests such as requests with missing line terminators.</td></tr><tr><td><code>403 Forbidden</code></td><td>Signifies that the client doesn't have appropriate access to the resource. It can also be returned when the server detects malicious input from the user.</td></tr><tr><td><code>404 Not Found</code></td><td>Returned when the client requests a resource that doesn't exist on the server.</td></tr><tr><td><code>500 Internal Server Error</code></td><td>Returned when the server cannot process the request.</td></tr></tbody></table>

<div data-full-width="true">

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

</div>

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Component</strong></td><td><strong>Example</strong></td><td><strong>Description</strong></td></tr><tr><td><code>Scheme</code></td><td><code>http://</code> <code>https://</code></td><td>This is used to identify the protocol being accessed by the client, and ends with a colon and a double slash (<code>://</code>)</td></tr><tr><td><code>User Info</code></td><td><code>admin:password@</code></td><td>This is an optional component that contains the credentials (separated by a colon <code>:</code>) used to authenticate to the host, and is separated from the host with an at sign (<code>@</code>)</td></tr><tr><td><code>Host</code></td><td><code>inlanefreight.com</code></td><td>The host signifies the resource location. This can be a hostname or an IP address</td></tr><tr><td><code>Port</code></td><td><code>:80</code></td><td>The <code>Port</code> is separated from the <code>Host</code> by a colon (<code>:</code>). If no port is specified, <code>http</code> schemes default to port <code>80</code> and <code>https</code> default to port <code>443</code></td></tr><tr><td><code>Path</code></td><td><code>/dashboard.php</code></td><td>This points to the resource being accessed, which can be a file or a folder. If there is no path specified, the server returns the default index (e.g. <code>index.html</code>).</td></tr><tr><td><code>Query String</code></td><td><code>?login=true</code></td><td>The query string starts with a question mark (<code>?</code>), and consists of a parameter (e.g. <code>login</code>) and a value (e.g. <code>true</code>). Multiple parameters can be separated by an ampersand (<code>&#x26;</code>).</td></tr><tr><td><code>Fragments</code></td><td><code>#status</code></td><td>Fragments are processed by the browsers on the client-side to locate sections within the primary resource (e.g. a header or section on the page).</td></tr></tbody></table>

curl z wykorzystaniem loginu i hasla

{% code overflow="wrap" fullWidth="true" %}
```
curl -H 'Authorization: Basic YWRtaW46YWRtaW4=' http://<SERVER_IP>:<PORT>/
curl -X POST -d 'username=admin&password=admin' http://<SERVER_IP>:<PORT>/
curl -X POST -d 'username=admin&password=admin' http://<SERVER_IP>:<PORT>/ -i

#With our authenticated cookie, we should now be able to interact with the web application without needing to provide our credentials every time. To test this, we can set the above cookie with the -b flag in cURL, as follows:
curl -b 'PHPSESSID=c1nsa6op7vtk7kdis7bcnbadf1' http://<SERVER_IP>:<PORT>/
curl -H 'Cookie: PHPSESSID=c1nsa6op7vtk7kdis7bcnbadf1' http://<SERVER_IP>:<PORT>/

#szukanie czegos metoda POST poprzez json
curl -X POST -d '{"search":"london"}' -b 'PHPSESSID=c1nsa6op7vtk7kdis7bcnbadf1' -H 'Content-Type: application/json' http://<SERVER_IP>:<PORT>/search.php
["London (UK)"]
```
{% endcode %}
