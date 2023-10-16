---
title: HTTP Server
tags:
  - standard-library
---

- Standard library HTTP juga tidak hanya digunakan untuk membuat HTTP Client, tapi juga digunakan untuk membuat HTTP Server.
- Untuk kasus sederhana, cocok sekali membuat HTTP Server menggunakan standard library Node.js, namun untuk kasus yang lebih kompleks, direkomendasikan menggunakan library atau framework yang lebih mudah penggunaannya.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/http.html

# File HTTP Server

```js
import http from "http";

const server = http.createServer((request, response) => {
  console.info(request.method);
  console.info(request.url);

  if (request.method === "POST") {
    request.addListener("data", (data) => {
      response.setHeader("Content-Type", "application/json");
      response.write(data);
      response.end();
    });
  } else {
    if (request.url === "aditya") {
      response.write("Hello aditya!");
    } else {
      response.write("Hello HTTP Server!");
    }
    response.end();
  }
});

server.listen(3000);
console.info("Server berjalan di port 3000");
```

# Test POST menggunakan REST Client

```http
POST http://localhost:3000
Content-Type: application/json
Accept: application/json
{
	"firstName": "Zulhaditya",
	"middleName": "Inayah",
	"lastName": "Hapiz"
}
```

**Selanjutnya :** [Cluster](cluster.md)
