---
tags:
  - JS
---
###### **Operator**

```js
let a = 7
let b = 2 

let sum = a + b
let difference = a -b
let product = a * b 
let quotient = a / b
let remainder = a % b

console.log("sum: " + sum)
console.log("difference: " + difference)
console.log("product: " + product)
console.log("quotient: " + quotient)
console.log("remainder: " + remainder)
```
$$
\begin{aligned}
sum: 9 \\
difference: 5 \\
product: 14 \\
quotient: 3.5 \\
remainder: 1
\end{aligned}
$$
###### **[Precedence Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_precedence)

###### **Assignment Operator**

| =   | Gán bằng   | x=1    | x =1      |
| --- | ---------- | ------ | --------- |
| +=  | Gán cộng   | x += y | x = x + y |
| -=  | Gán trừ    | x -= y | x = x - y |
| *=  | Gán nhân   | x *= y | x = x * y |
| /=  | Gán chia   | x /= y | x = x / y |
| %=  | Gán lấy dư | x %= y | x = x % y |

###### **Increment and Decrement Operators**

**Prefix & Posfix**
- a *++* , a *--*     -->  **Posfix**
- *++* a, *--* a      -->  **Prefix**

**Precedence**
- *Step 1:* **Prefix**
- *Step 2:* **Phép toán khác**
- *Step 3:* **Gán giá trị cho biến bên trái dấu =**
- *Step 4:* **Posfix**

```js
let a 
```