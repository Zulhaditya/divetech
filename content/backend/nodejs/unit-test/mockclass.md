---
title: Mock Class
tags:
  - jest
---

- Jest juga bisa digunakan untuk melakukan Mock Class.
- Seperti yang sudah kita pelajari di javascript OOP, Class di javascript sebenarnya adalah constructor function, yang sebenarnya tidak ada bedanya dengan function biasanya.
- Oleh karena itu, untuk melakukan mock class, sama saja seperti melakukan mock function.

## user-repository.js

```js
export class UserRepository {
  save(user) {
    throw new Error("Not implemented");
  }

  findById(id) {
    throw new Error("Not implemented");
  }

  findAll() {
    throw new Error("Not implemented");
  }
}
```

## user-service.js

```js
import { UserRepository } from "./user-repository";

export class UserService {
  constructor(userRepository) {
    if (userRepository) {
      this.userRepository = userRepository;
    } else {
      this.userRepository = new UserRepository();
    }
  }
  save(user) {
    this.userRepository.save(user);
  }
  findById(id) {
    return this.userRepository.findById(id);
  }
  findAll() {
    return this.userRepository.findAll();
  }
}
```

## mock-class.test.js

```js
import { UserRepository } from "../src/user-repository";
import { UserService } from "../src/user-service";

jest.mock("../src/user-repository");

const repository = new UserRepository();
const service = new UserService(repository);

test("test mock user save", () => {
  const user = {
    id: 1,
    name: "Inayah",
  };
  service.save(user);

  expect(repository.save).toHaveBeenCalled();
  expect(repository.save).toHaveBeenCalledWith(user);
});

test("test mock class findById", () => {
  const user = {
    id: 1,
    name: "Zulhaditya",
  };
  repository.findById.mockReturnValueOnce(user);

  expect(service.findById(1)).toEqual(user);
  expect(repository.findById).toHaveBeenCalled();
  expect(repository.findById).toHaveBeenCalledWith(1);
});

test("test mock class findAll", () => {
  const users = [
    {
      id: 1,
      name: "Zulhaditya",
    },
    {
      id: 2,
      name: "Inayah",
    },
  ];
  repository.findAll.mockReturnValueOnce(users);

  expect(service.findAll()).toEqual(users);
  expect(repository.findAll).toHaveBeenCalled();
});
```

**Selanjutnya :** [Mock Partial Class](mockpartialclass.md)
