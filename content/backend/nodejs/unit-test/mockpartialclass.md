---
title: Mock Partial Class
tags:
  - jest
---

- Saat kita melakukan mock class dengan melakukan modules, secara otomatis semua function di class tersebut akan ter-mock.
- Kadang, misalkan ada kasus dimana kita ingin melakukan mock hanya sebagian function saja di dalam class.
- Pada kasus ini, kita bisa menggunakan jest.spyOn()
- https://jestjs.io/docs/jest-object#jestspyonobject-methodname

```js
import { UserRepository } from "../src/user-repository";
import { UserService } from "../src/user-service";

const repository = new UserRepository();
const service = new UserService(repository);

test("test mock partial class findById", () => {
  const user = {
    id: 1,
    name: "Inayah",
  };
  const findByIdMock = jest.spyOn(repository, "findById");
  findByIdMock.mockReturnValueOnce(user);

  expect(service.findById(1)).toEqual(user);
  expect(findByIdMock).toHaveBeenCalled();
  expect(findByIdMock).toHaveBeenCalledWith(1);
  expect(repository.findById).toHaveBeenCalled();
  expect(repository.findById).toHaveBeenCalledWith(1);
});

test.failing("test mock partial findAll", () => {
  service.findAll();
});
```
