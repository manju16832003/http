# HTTP CORS


### Preflighted Requests

"Preflighted" requests first send an HTTP request by the OPTIONS method to the resource on the other domain, 
in order to determine whether the actual request is safe to send. Cross-site requests are Preflighted like 
this since they may have implications to user data.

*Cross-site requests are Preflighted*

In particular, a request is Preflighted if *any of the following conditions* are true

- PUT
- DELETE
- CONNECT
- OPTIONS
- TRACE
- PATCH


if the request includes the following

- Accept
- Accept-Language
- Content-Language
- Content-Type
- DPR
- Downlink
- Save-Data
- Viewport-Width
- Width

Or if the `Content-Type` header has a value other the following
- applicaiton/x-www-form-urlencoded
- multipart/form-data
- text/plain

Or if one or more event listeners are registered on an XMLHttpRequestUpload object used in the request.

Or if a ReadableStream object is used in the request


Following Example of a request that will be preflighted

```
  var invocation = new XMLHttpRequest();
  var url = 'http://bar.other/resources/post-here/';
  var body = '<?xml version="1.0"?><person><name>Arun</name></person>';
      
  function callOtherDomain(){
    if(invocation)
      {
        invocation.open('POST', url, true);
        invocation.setRequestHeader('X-PINGOTHER', 'pingpong');
        invocation.setRequestHeader('Content-Type', 'application/xml');
        invocation.onreadystatechange = handler;
        invocation.send(body); 
      }
  }
```

### Reqeusts with credentials

`Access-Control-Allow-Credentials: true`

GET http://foo.com
  -> Trying to connec to GET http://bar.com

  http://bar.com must respond with `Access-Control-Allow-Origin: true` inorder for foo.com to access to bar.com even if its GET request

  Reference: https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#Preflighted_requests