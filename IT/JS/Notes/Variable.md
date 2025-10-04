---
tags:
  - JS
---
*Có 3 variable phổ biến hiện nay*
- **Var
- **Let
- **Const ?(cần được khởi tạo giá trị từ đầu ~ không được khai báo)

###### *Khai báo variable*
- **Chỉ đặt tên và chưa cho giá trị
```js
var yourName
```

###### *Khởi tạo variable*
- **Khai báo và thêm giá trị
```js 
var yourName = "lepuong"
let yourAge = "halfALife"
const real = 21
```

###### *Export variable*
```js
let a = 5, b = 10, c = a + b
```
- **Cách 1
```js
Cconsole.log(a + " + " + b + " = " + c)
```
- **Cách 2
```js
Cconsole.log(a , "+" , b , "=" , c)
```
- **Cách 3
```js
Cconsole.log(`${a} + ${b} = ${c}`)
```
- **Cách 4
```js
Cconsole.log(`%s + %s = %s`, a, b, c)
```