---
tags:
  - JS
  - Functions
---
ví dụ như từ **String** sang **int**


###### parseInt
*có thể dùng **parseInt(value, radix)** kiểu dữ liệu khác sang **int***
- Tham số thứ 2 chỉ định hệ số (base) của hệ thống số
	- 2 -> hệ nhị phân (binary)
	- 8 -> hệ bát phân (octal)
	- 10 -> hệ thập phân (decimal) (mặc định)
	- 16 -> hệ thập lục phân (hexadecimal)
- nếu ký tự đầu tiên không chuyển đổi được sẽ trả về *NaN* ^3eb926
- Bỏ qua khoảng trắng đầu và cuối chuỗi ^b4fb7a
```js
let varA = "9"
console.log(parseInt(varA),10)
```

###### parseFloat
*dùng **parseFloat()** kiểu dữ liệu khác sang **float***
```js
let varA = "9"
console.log(parseFloat(varA))
```
- [[#^3eb926]]
- [[#^b4fb7a]]

###### Number
*dùng **Number()** kiểu dữ liệu khác sang **number***
```js
let varA = true
console.log(Number(varA))
```
- [[#^3eb926]]
- Nếu là *Booleans*, thì sẽ trả về **0**, **1**
- Nếu là *dates* , thì trả về số minisecond từ **1/1/1970**.
- Nếu là *string* thì trả về **NaN**

###### String
*dùng **String()** kiểu dữ liệu khác sang **String** tương đương với [[toString()]]*
```js
let varA = true
console.log(String(varA))
```