# HTTP client example

## Build

```
cargo build --target wasm32-wasi --release
```

## Run

```
$ wasmedge target/wasm32-wasi/release/wasmedge_hyper_client.wasm

GET as byte stream: http://eu.httpbin.org/get?msg=Hello
Response: 200 OK
Headers: {
    "date": "Mon, 26 Sep 2022 02:44:18 GMT",
    "content-type": "application/json",
    "content-length": "236",
    "connection": "keep-alive",
    "server": "gunicorn/19.9.0",
    "access-control-allow-origin": "*",
    "access-control-allow-credentials": "true",
}

b"{\n  \"args\": {\n    \"msg\": \"Hello\"\n  }, \n  \"headers\": {\n    \"Host\": \"eu.httpbin.org\", \n    \"X-Amzn-Trace-Id\": \"Root=1-63311202-67b10bb4094002892eeb9a51\"\n  }, \n  \"origin\": \"13.87.135.123\", \n  \"url\": \"http://eu.httpbin.org/get?msg=Hello\"\n}\n"

GET and get result as string: http://eu.httpbin.org/get?msg=WasmEdge
{
  "args": {
    "msg": "WasmEdge"
  },
  "headers": {
    "Host": "eu.httpbin.org",
    "X-Amzn-Trace-Id": "Root=1-63311202-548ac9433669e7112347fbda"
  },
  "origin": "13.87.135.123",
  "url": "http://eu.httpbin.org/get?msg=WasmEdge"
}


POST and get result as string: http://eu.httpbin.org/post
with a POST body: hello wasmedge
{
  "args": {},
  "data": "hello wasmedge",
  "files": {},
  "form": {},
  "headers": {
    "Content-Length": "14",
    "Host": "eu.httpbin.org",
    "X-Amzn-Trace-Id": "Root=1-63311202-3b0eb3ee1cb609f63db9dcb5"
  },
  "json": null,
  "origin": "13.87.135.123",
  "url": "http://eu.httpbin.org/post"
}
```

