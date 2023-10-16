---
title: Events
tags:
  - standard-library
---

- Events adalah standard library yang digunakan untuk implementasi Event Listener.
- Didalam Events, terdapat sebuah class bernama EventEmitter yang bisa digunakan untuk menampung data listener per jenis event.
- Kita bisa melakukan emmit untuk mentrigger jenis event dan mengirim data ke event tersebut
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/events.html

```js
import EventEmitter from "events";

const emitter = new EventEmitter();

emitter.addListener("hello", (name) => {
  console.info(`Hello ${name}`);
});

emitter.addListener("hello", (name) => {
  console.info(`Halo ${name}`);
});

emitter.emit("hello", "Aditya");
```

**Selanjutnya :** [Globals](globals.md)