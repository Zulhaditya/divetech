---
title: Setup Node.js
tags:
  - typescript
---

# Membuat Project Node.js

## 1. Buat Folder

Buatlah sebuah folder learn-typescript. Jika menggunakan **Linux** atau **Mac** bisa gunakan perintah dibawah ini:

```bash
mkdir learn-typescript
```

## 2. Inisialisasi Project

Buat project **Node.js** didalam folder tersebut dengan perintah:

```bash
npm init
```

## 3. Tambah Type Module

Selanjutnya buka **package.json** dan tambah type module:

```json
{
  "name": "learn-typescript",
  "version": "1.0.0",
  "description": "Learn typescript",
  "main": "index.js",
  "type": "module",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Zulhaditya",
  "license": "ISC"
}
```

## 4. Install Jest

Menambahkan library **Jest** untuk melakukan unit test pada kode TypeScript kita:

```bash
npm install --save-dev jest @types/jest
```

## 5. Install Babel

Menambahkan library **Babel** agar **Jest** support JavaScript library module:

```bash
npm install --save-dev babel-jest @babel/preset-env
```

## 6. Setup Babel

Buka link ini: https://babeljs.io/setup#installation dan lihat section **Test Framework**, klik **Jest**. Pada **package.json** tambahkan kode berikut:

```json
{
  "scripts": {
    "test": "jest"
  },
  "jest": {
    "transform": {
      "^.+\\.[t|j]sx?$": "babel-jest"
    }
  }
}
```

Kode **package.json** akan menjadi seperti ini:

```json
{
  "name": "typescript",
  "version": "1.0.0",
  "description": "Learn typescript",
  "main": "index.js",
  "type": "module",
  "scripts": {
    "test": "jest"
  },
  "jest": {
    "transform": {
      "^.+\\.[t|j]sx?$": "babel-jest"
    }
  },
  "author": "Zulhaditya",
  "license": "ISC",
  "devDependencies": {
    "@babel/preset-env": "^7.23.2",
    "@types/jest": "^29.5.5",
    "babel-jest": "^29.7.0",
    "jest": "^29.7.0"
  }
}
```

## 7. Buat Config Babel

Buatlah sebuah file **babel.config.json** pada project TypeScript tadi untuk mengaktifkan fitur preset babel:

```json
{
  "presets": ["@babel/preset-env"]
}
```

**Selanjutnya** : [Setup TypeScript](/backend/typescript/setuptypescript)
