Skip to content
OkHttp
Overview


logoOkHttp
 OkHttp
44.5k9.2k
Overview
Overview
Overview
Table of contents
Get a URL
Post to a Server
Requirements
Releases
MockWebServer
GraalVM Native Image
License
Stack Overflow
Features
Features
Calls
Caching
Connections
Events
HTTPS
Interceptors
Recipes
Security
Security
Security
Providers
Configuration History
Works with OkHttp
API
API
okhttp
brotli
dnsoverhttps
logging-interceptor
sse
tls
urlconnection
mockwebserver
Change Logs
Change Logs
Change Log
4.x Change Log
Upgrading to OkHttp 4
3.x Change Log
2.x Change Log
1.x Change Log
Contributing
Contributing
Contributing
Code of Conduct
Concurrency
Debug Logging
OkHttp¶
HTTP is the way modern applications network. It’s how we exchange data & media. Doing HTTP efficiently makes your stuff load faster and saves bandwidth.

OkHttp is an HTTP client that’s efficient by default:

HTTP/2 support allows all requests to the same host to share a socket.
Connection pooling reduces request latency (if HTTP/2 isn’t available).
Transparent GZIP shrinks download sizes.
Response caching avoids the network completely for repeat requests.
OkHttp perseveres when the network is troublesome: it will silently recover from common connection problems. If your service has multiple IP addresses, OkHttp will attempt alternate addresses if the first connect fails. This is necessary for IPv4+IPv6 and services hosted in redundant data centers. OkHttp supports modern TLS features (TLS 1.3, ALPN, certificate pinning). It can be configured to fall back for broad connectivity.

Using OkHttp is easy. Its request/response API is designed with fluent builders and immutability. It supports both synchronous blocking calls and async calls with callbacks.

Get a URL¶
This program downloads a URL and prints its contents as a string. Full source.


OkHttpClient client = new OkHttpClient();

String run(String url) throws IOException {
  Request request = new Request.Builder()
      .url(url)
      .build();

  try (Response response = client.newCall(request).execute()) {
    return response.body().string();
  }
}
Post to a Server¶
This program posts data to a service. Full source.


public static final MediaType JSON
    = MediaType.get("application/json; charset=utf-8");

OkHttpClient client = new OkHttpClient();

String post(String url, String json) throws IOException {
  RequestBody body = RequestBody.create(json, JSON);
  Request request = new Request.Builder()
      .url(url)
      .post(body)
      .build();
  try (Response response = client.newCall(request).execute()) {
    return response.body().string();
  }
}
Further examples are on the OkHttp Recipes page.

Requirements¶
OkHttp works on Android 5.0+ (API level 21+) and Java 8+.

OkHttp depends on Okio for high-performance I/O and the Kotlin standard library. Both are small libraries with strong backward-compatibility.

We highly recommend you keep OkHttp up-to-date. As with auto-updating web browsers, staying current with HTTPS clients is an important defense against potential security problems. We track the dynamic TLS ecosystem and adjust OkHttp to improve connectivity and security.

OkHttp uses your platform’s built-in TLS implementation. On Java platforms OkHttp also supports Conscrypt, which integrates BoringSSL with Java. OkHttp will use Conscrypt if it is the first security provider:


Security.insertProviderAt(Conscrypt.newProvider(), 1);
The OkHttp 3.12.x branch supports Android 2.3+ (API level 9+) and Java 7+. These platforms lack support for TLS 1.2 and should not be used. But because upgrading is difficult, we will backport critical fixes to the 3.12.x branch through December 31, 2021.

Releases¶
Our change log has release history.

The latest release is available on Maven Central.


implementation("com.squareup.okhttp3:okhttp:4.10.0")
Snapshot builds are available. R8 and ProGuard rules are available.

Also, we have a bill of materials (BOM) available to help you keep OkHttp artifacts up to date and be sure about version compatibility.


    dependencies {
       // define a BOM and its version
       implementation(platform("com.squareup.okhttp3:okhttp-bom:4.10.0"))

       // define any required OkHttp artifacts without version
       implementation("com.squareup.okhttp3:okhttp")
       implementation("com.squareup.okhttp3:logging-interceptor")
    }
MockWebServer¶
OkHttp includes a library for testing HTTP, HTTPS, and HTTP/2 clients.

The latest release is available on Maven Central.


testImplementation("com.squareup.okhttp3:mockwebserver:4.10.0")
GraalVM Native Image¶
Building your native images with Graal https://www.graalvm.org/ should work automatically. This is not currently in a final released version, so 5.0.0-alpha.2 should be used. Please report any bugs or workarounds you find.

See the okcurl module for an example build.


$ ./gradlew okcurl:nativeImage
$ ./okcurl/build/graal/okcurl https://httpbin.org/get
License¶

Copyright 2019 Square, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
NextCalls
Copyright © 2022 Block, Inc.
Made with Material for MkDocs
web: gunicorn blockexplorer.wsgi
