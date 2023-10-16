---
title: Net
tags:
  - standard-library
---

- Net merupakan standard library yang bisa digunakan untuk membuat network client dan server berbasis TCP.
- Net server dan client merupakan object stream, sehingga kita bisa baca datanya, tulis datanya, dan juga menambahkan listener.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/net.html

# Net Server

```js
// net-server.mjs
import net from "net";

const server = net.createServer((client) => {
  console.info("Client connected");

  client.addListener("data", (data) => {
    console.info(`Receive data ${data.toString()}`);
    client.write(`Hello ${data.toString()}\r\n`);
  });
});

server.listen(3000, "localhost");
```

# Net Client

```js
// net-client.mjs
import net from "net";

const client = net.createConnection({
  port: 3000,
  host: "localhost",
});

client.addListener("data", (data) => {
  console.info(`Receive data from server: ${data.toString()}`);
});

setInterval(() => {
  client.write(`${process.argv[2]}\r\n`);
}, 2000);
```

**Selanjutnya :** [URL](url.md)