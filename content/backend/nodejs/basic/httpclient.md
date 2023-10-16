---
title: HTTP Client
tags:
  - standard-library
---

- Node.js memiliki standard library untuk HTTP.
- Salah satu fitur di module HTTP adalah HTTP Client, dimana kita bisa melakukan simulasi HTTP Request menggunakan Node.js
- Terdapat 2 jenis module HTTP di Node.js, yaitu HTTP dan HTTPS.
- Resources HTTP: https://nodejs.org/dist/latest-v16.x/docs/api/http.html
- Resources HTTPS: https://nodejs.org/dist/latest-v16.x/docs/api/https.html

```js
import https from "https";

const endpoint = "https://eo2mf6at880v5su.m.pipedream.net";

const request = https.request(
  endpoint,
  {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Accept: "application/json",
    },
  },
  (response) => {
    response.addListener("data", (data) => {
      console.info(`Receive data: ${data.toString()}`);
    });
  }
);

const body = JSON.stringify({
  firstName: "Inayah",
  lastName: "Wulandari",
});

request.write(body);
request.end();
```

**Selanjutnya :** [HTTP Server](httpserver.md)