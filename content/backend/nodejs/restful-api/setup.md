---
title: Setup
tags:
  - api
---

# 1. Setup Prisma

Buat folder src/application yang berisikan tiga file yaitu:

- database.js
- logging.js
- web.js

## database.js

```js
import { PrismaClient } from "@prisma/client";

import { logger } from "./logging";

export const prismaClient = new PrismaClient({
  log: [
    {
      emit: "event",
      level: "query",
    },
    {
      emit: "event",
      level: "error",
    },
    {
      emit: "event",
      level: "info",
    },
    {
      emit: "event",
      level: "warn",
    },
  ],
});

prismaClient.$on("error", (e) => {
  logger.error(e);
});

prismaClient.$on("warn", (e) => {
  logger.warn(e);
});

prismaClient.$on("info", (e) => {
  logger.info(e);
});

prismaClient.$on("query", (e) => {
  logger.info(e);
});
```

## logging.js

```js
import winston from "winston";

export const logger = winston.createLogger({
  level: "info",
  format: winston.format.json(),
  transports: [new winston.transports.Console({})],
});
```

## web.js

```js
import express from "express";

export const web = express();
web.use(express.json());
```
