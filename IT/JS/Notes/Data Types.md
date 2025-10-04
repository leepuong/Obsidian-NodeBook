---
tags:
  - JS
---


##### **Primitive Data Types**

###### **String**
- *Kiểu chuỗi* kiểu dữ liệu để lưu trữ chuỗi ký tự
```js
let myString1 = "hello"
let myString2 = 'hello'
let myString3 = `hello`
console.log(typeof myString1)
console.log(typeof myString2)
console.log(typeof myString3)
```
$$string$$
###### **Number**
- *Kiểu số* Kiểu dữ liệu để lưu trữ số, có thể là số nguyên hoặc số thực
```js
let soNguyen = 12
let soThuc = 10.26
console.log(typeof soNguyen)
console.log(typeof soThuc)
```
$$number$$
- *Number* có giá trị tối đa và tổi thiểu từ $2^{53} -1$ đến $-(2^{53}-1)$ tương đương:
```js
console.log(Number.MIN_SAFE_INTEGER + " to " + Number.MAX_SAFE_INTEGER)
```
$$-9007199254740991 \quad to \quad 9007199254740991$$
###### **Boolean**
- *Kiểu luận lý* Chỉ có thể là **true** hoặc **false** 
```js
let isTrue = true
let isFalse = false
console.log(typeof isTrue)
console.log(typeof isFalse)
```
$$boolean$$
###### **Undefined**
- [[Variable]] chưa được gán dữ liệu sẽ có kiểu dữ liệu là **Undefined**
```js
let undefinedValue
console.log(typeof undefinedValue)
```
$$undefined$$
###### **Null**
- Thường dùng để reset [[Variable]] 
```js
let nullValue = null
console.log(typeof nullValue)
```
$$null$$

