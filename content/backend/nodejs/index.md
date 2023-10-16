---
title: Dokumentasi Node.js
tags:
  - nodejs
---

- Node.js adalah runtime environment untuk JavaScript yang bersifat open-source dan cross-platform
- Dengan Node.js kita dapat menjalankan kode JavaScript di mana pun, tidak hanya terbatas pada lingkungan browser
- Download Node.js [disini](https://nodejs.org/en/download)

Node.js juga menyediakan banyak library/module JavaScript yang membantu pembuatan aplikasi web. Berikut ini adalah beberapa fitur penting dari Node.js yang menjadikannya pilihan utama dalam pengembangan aplikasi:

- **Asynchronous & Event-driven**

  Semua API dari Node.js bersifat asynchronous, artinya tidak memblokir proses lain sembari menunggu satu proses selesai. Server Node.js akan melanjutkan ke ke pemanggilan API berikutnya lalu memanfaatkan mekanisme event notification untuk mendapatkan respon dari panggilan API sebelumnya.

- **Fast**

  Eksekusi kode dengan Node.js sangat cepat karena berjalan pada V8 JavaScript Engine dari Google Chrome.

- **Single Threaded but Highly Scalable**

  Node.js menggunakan model single thread dengan event looping. Mekanisme ini membantu server untuk merespon secara asynchronous dan menjadikan server lebih scalable dibandingkan server tradisional yang menggunakan banyak thread untuk menangani permintaan.

# Basic

| **Basic**                                                      | **Standard Library**                          |                                                    |
| -------------------------------------------------------------- | --------------------------------------------- | -------------------------------------------------- |
| [Intro](/backend/nodejs/basic/intro.md)                        | [Path](/backend/nodejs/basic/path.md)         | [Stream](/backend/nodejs/basic/stream.md)          |
| [Arsitektur](/backend/nodejs/basic/arsitektur.md)              | [File System](/backend/nodejs/basic/fs.md)    | [Net](/backend/nodejs/basic/net.md)                |
| [Node REPL](/backend/nodejs/basic/repl.md)                     | [Debugger](/backend/nodejs/basic/debugger.md) | [URL](/backend/nodejs/basic/url.md)                |
| [Module System](/backend/nodejs/basic/modulesystem.md)         | [DNS](/backend/nodejs/basic/dns.md)           | [Util](/backend/nodejs/basic/util.md)              |
| [Concurrency & Parallel](/backend/nodejs/basic/concurrency.md) | [Events](/backend/nodejs/basic/events.md)     | [Zlib](/backend/nodejs/basic/zlib.md)              |
| [Threadpool Web Model](/backend/nodejs/basic/threadpool.md)    | [Globals](/backend/nodejs/basic/globals.md)   | [Console](/backend/nodejs/basic/console.md)        |
| [Blocking & Non-Blocking](/backend/nodejs/basic/blocking.md)   | [Process](/backend/nodejs/basic/process.md)   | [Worker Threads](/backend/nodejs/basic/worker.md)  |
| [Global Async](/backend/nodejs/basic/globalasync.md)           | [Readline](/backend/nodejs/basic/readline.md) | [HTTP Client](/backend/nodejs/basic/httpclient.md) |
| [Standard Library](/backend/nodejs/basic/standardlib.md)       | [Report](/backend/nodejs/basic/report.md)     | [HTTP Server](/backend/nodejs/basic/httpserver.md) |
| [OS](/backend/nodejs/basic/os.md)                              | [Buffer](/backend/nodejs/basic/buffer.md)     | [Cluster](/backend/nodejs/basic/cluster.md)        |

# NPM

| **Project**                                            | **Dependency**                                                 |
| ------------------------------------------------------ | -------------------------------------------------------------- |
| [Intro](/backend/nodejs/npm/intro.md)                  | [Export Module](/backend/nodejs/npm/exportmodule.md)           |
| [Project Config](/backend/nodejs/npm/projectconfig.md) | [Dependency Management](/backend/nodejs/npm/dependency.md)     |
| [Project Type](/backend/nodejs/npm/projecttype.md)     | [Dependency Version](/backend/nodejs/npm/dependencyversion.md) |
| [Script](/backend/nodejs/npm/script.md)                | [Development Dependency](/backend/nodejs/npm/dependencydev.md) |
| [Ignore File](/backend/nodejs/npm/ignorefile.md)       | [Package](/backend/nodejs/npm/package.md)                      |

# Unit Test

| **Setup**                                                               | **Matchers**                                                          | **Mock**                                                            |
| ----------------------------------------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [Software Testing](/backend/nodejs/unit-test/softwaretesting.md)        | [Numbers Matchers](/backend/nodejs/unit-test/numbersmatcher.md)       | [Skip Function](/backend/nodejs/unit-test/skipfunction.md)          |
| [Pengenalan Jest](/backend/nodejs/unit-test/intro.md)                   | [Strings Matchers](/backend/nodejs/unit-test/stringmatchers.md)       | [Only Function](/backend/nodejs/unit-test/onlyfunction.md)          |
| [Install Jest](/backend/nodejs/unit-test/install.md)                    | [Array Matchers](/backend/nodejs/unit-test/arraymatchers.md)          | [Duplicate Unit Test](/backend/nodejs/unit-test/duplicate.md)       |
| [Buat Unit Test](/backend/nodejs/unit-test/create.md)                   | [Exceptions Matchers](/backend/nodejs/unit-test/exceptionmatchers.md) | [Concurrent Test](/backend/nodejs/unit-test/concurrent.md)          |
| [Jest Configuration](/backend/nodejs/unit-test/jestconfig.md)           | [Not Matchers](/backend/nodejs/unit-test/notmatchers.md)              | [Todo Function](/backend/nodejs/unit-test/todofunction.md)          |
| [Pengenalan Babel](/backend/nodejs/unit-test/introbabel.md)             | [Test Async Code](/backend/nodejs/unit-test/testasync.md)             | [Failing Function](/backend/nodejs/unit-test/failingfunction.md)    |
| [Jest CLI](/backend/nodejs/unit-test/jestcli.md)                        | [Setup Function](/backend/nodejs/unit-test/setupfunction.md)          | [Mock](/backend/nodejs/unit-test/mock.md)                           |
| [Matchers](/backend/nodejs/unit-test/matchers.md)                       | [Scoping](/backend/nodejs/unit-test/scoping.md)                       | [Mock Function](/backend/nodejs/unit-test/mockfunction.md)          |
| [Equal Matchers](/backend/nodejs/unit-test/equalmatchers.md)            | [Code Coverage](/backend/nodejs/unit-test/codecoverage.md)            | [Mock Matchers](/backend/nodejs/unit-test/mockmatchers.md)          |
| [Truthiness Matchers](/backend/nodejs/unit-test/truthiness.md)          | [It Function](/backend/nodejs/unit-test/itfunction.md)                | [Mock Modules](/backend/nodejs/unit-test/mockmodules.md)            |
| [Mock Partial Modules](/backend/nodejs/unit-test/mockpartialmodules.md) | [Mock Class](/backend/nodejs/unit-test/mockclass.md)                  | [Mock Partial Class](/backend/nodejs/unit-test/mockpartialclass.md) |

# Logging

| **Logger**                                                       | **Transport**                                                   |
| ---------------------------------------------------------------- | --------------------------------------------------------------- |
| [Intro Logging](/backend/nodejs/logging/intro.md)                | [File Transport](/backend/nodejs/logging/filetransport.md)      |
| [Logging Library](/backend/nodejs/logging/logginglib.md)         | [Transport Level](/backend/nodejs/logging/transportlevel.md)    |
| [Logger](/backend/nodejs/logging/logger.md)                      | [Rotate File](/backend/nodejs/logging/rotatefile.md)            |
| [Console Transport](/backend/nodejs/logging/consoletransport.md) | [Membuat Transport](/backend/nodejs/logging/createtransport.md) |
| [Logging Level](/backend/nodejs/logging/logginglevel.md)         | [Exceptions](/backend/nodejs/logging/exceptions.md)             |
| [Format](/backend/nodejs/logging/format.md)                      | [Rejections](/backend/nodejs/logging/rejections.md)             |
| [Combine Format](/backend/nodejs/logging/combineformat.md)       |                                                                 |

# Express

| **Request**                                                    | **Response**                                                    | **Route**                                                           |
| -------------------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------- |
| [Intro ExpressJS](/backend/nodejs/express/intro.md)            | [Response Header](/backend/nodejs/express/responseheader.md)    | [Cookie](/backend/nodejs/express/cookie.md)                         |
| [Application](/backend/nodejs/express/application.md)          | [Response Body](/backend/nodejs/express/responsebody.md)        | [Signed Cookie](/backend/nodejs/express/signedcookie.md)            |
| [Basic Routing](/backend/nodejs/express/basicrouting.md)       | [Redirect](/backend/nodejs/express/redirect.md)                 | [Response Body Lainnya](/backend/nodejs/express/responselainnya.md) |
| [Unit Test](/backend/nodejs/express/unittest.md)               | [Middleware](/backend/nodejs/express/middleware.md)             | [Error Handling](/backend/nodejs/express/errorhandling.md)          |
| [Request](/backend/nodejs/express/request.md)                  | [Route Path](/backend/nodejs/express/routepath.md)              | [Static File](/backend/nodejs/express/staticfile.md)                |
| [Request URL](/backend/nodejs/express/requesturl.md)           | [Route Parameter](/backend/nodejs/express/routeparameter.md)    | [Template Engine](/backend/nodejs/express/templateengine.md)        |
| [Request Query Param](/backend/nodejs/express/requestparam.md) | [Route Function](/backend/nodejs/express/routefunction.md)      | [File Upload](/backend/nodejs/express/fileupload.md)                |
| [Request Header](/backend/nodejs/express/requestheader.md)     | [Router](/backend/nodejs/express/router.md)                     | [Not Found Error](/backend/nodejs/express/notfound.md)              |
| [Response](/backend/nodejs/express/response.md)                | [Type of Middleware](/backend/nodejs/express/typemiddleware.md) |                                                                     |
| [Response Status](/backend/nodejs/express/responsestatus.md)   | [Request Body](/backend/nodejs/express/requestbody.md)          |                                                                     |

# Mustache

| **Setup**                                                      | **Function**                                                      |
| -------------------------------------------------------------- | ----------------------------------------------------------------- |
| [Intro Mustache](/backend/nodejs/mustache/intro.md)            | [Section Data](/backend/nodejs/mustache/sectiondata.md)           |
| [Penggunaan Mustache](/backend/nodejs/mustache/usemustache.md) | [Inverted Sections](/backend/nodejs/mustache/invertedsections.md) |
| [Mustache Cache](/backend/nodejs/mustache/mustachecache.md)    | [List](/backend/nodejs/mustache/list.md)                          |
| [Tags](/backend/nodejs/mustache/tags.md)                       | [List Object](/backend/nodejs/mustache/listobject.md)             |
| [Nested Object](/backend/nodejs/mustache/nestedobject.md)      | [Functions](/backend/nodejs/mustache/functions.md)                |
| [Mustache File](/backend/nodejs/mustache/mustachefile.md)      | [Comment](/backend/nodejs/mustache/comment.md)                    |
| [Sections](/backend/nodejs/mustache/sections.md)               | [Partials](/backend/nodejs/mustache/partials.md)                  |

# Database

| **Setup**                                                             | **Function**                                              | **Relationship**                                                               |
| --------------------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [Intro NodeJS Database](/backend/nodejs/database/intro.md)            | [Prisma ORM](/backend/nodejs/database/prismaorm.md)       | [Where Condition dan Operator](/backend/nodejs/database/wherecondition.md)     |
| [Pengenalan ORM](/backend/nodejs/database/introorm.md)                | [Model](/backend/nodejs/database/model.md)                | [Prisma Schema](/backend/nodejs/database/prismaschema.md)                      |
| [Pengenalan Prisma](/backend/nodejs/database/introprisma.md)          | [CRUD](/backend/nodejs/database/crud.md)                  | [Auto Increment](/backend/nodejs/database/autoincrement.md)                    |
| [Install Prisma](/backend/nodejs/database/installprisma.md)           | [Transaction](/backend/nodejs/database/transaction.md)    | [One to One Relationship](/backend/nodejs/database/onetoone.md)                |
| [Database Connection](/backend/nodejs/database/databaseconnection.md) | [CRUD Many](/backend/nodejs/database/crudmany.md)         | [One to Many Relationship](/backend/nodejs/database/onetomany.md)              |
| [Generate](/backend/nodejs/database/generate.md)                      | [Paging](/backend/nodejs/database/paging.md)              | [Many to Many Relationship](/backend/nodejs/database/manytomany.md)            |
| [Prisma Client](/backend/nodejs/database/prismaclient.md)             | [Sorting](/backend/nodejs/database/sorting.md)            | [Prisma Migrate](/backend/nodejs/database/prismamigrate.md)                    |
| [Tag Function](/backend/nodejs/database/tagfunction.md)               | [Select Fields](/backend/nodejs/database/selectfields.md) | [Model-first Migration](/backend/nodejs/database/modelfirstmigration.md)       |
| [Execute SQL](/backend/nodejs/database/executesql.md)                 | [Count](/backend/nodejs/database/count.md)                | [Database-first Migration](/backend/nodejs/database/databasefirstmigration.md) |
| [Query SQL](/backend/nodejs/database/querysql.md)                     | [Aggregate](/backend/nodejs/database/aggregate.md)        | [Prisma Studio](/backend/nodejs/database/prismastudio.md)                      |

# Validation

| **Validation**                                                      | **Options**                                                                          |
| ------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| [Intro Validation](/backend/nodejs/validation/intro.md)             | [Validation Option](/backend/nodejs/validation/validationoption.md)                  |
| [Validation](/backend/nodejs/validation/validation.md)              | [Object Validation](/backend/nodejs/validation/objectvalidation.md)                  |
| [Date Validation](/backend/nodejs/validation/datevalidation.md)     | [Array Validation](/backend/nodejs/validation/arrayvalidation.md)                    |
| [Validation Result](/backend/nodejs/validation/validationresult.md) | [Custom Validation Messages](/backend/nodejs/validation/customvalidationmessages.md) |
| [Validation Error](/backend/nodejs/validation/validationerror.md)   | [Custom Validation](/backend/nodejs/validation/customvalidation.md)                  |

# Restful API

| **Requirement**                                                                    | **Model**                                                         |
| ---------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| [Requirement](/backend/nodejs/restful-api/requirement.md)                          | [User API Spec](/backend/nodejs/restful-api/userapispec.md)       |
| [User Management Requirement](/backend/nodejs/restful-api/usermanagement.md)       | [Contact API Spec](/backend/nodejs/restful-api/contactapispec.md) |
| [Contact Management Requirement](/backend/nodejs/restful-api/contactmanagement.md) | [Address API Spec](/backend/nodejs/restful-api/addressapispec.md) |
| [Address Management Requirement](/backend/nodejs/restful-api/addressmanagement.md) | [Create Model](/backend/nodejs/restful-api/createmodel.md)        |
| [Membuat Project](/backend/nodejs/restful-api/create.md)                           | [10 - Setup Project](/backend/nodejs/restful-api/setup.md)        |
