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
- Đối với *Posfix* thì giá trị thường được thay đổi sau khi quá trình tính toán và sử dụng hoàn thành, cho nên giá trị được sử dụng không phải là giá trị sau khi thực hiện *Posfix* mà là giá trị trước khi *posfix*.

**Precedence**
- *Step 1:* **Prefix** ^737316
- *Step 2:* **Phép toán khác** ^6ce668
- *Step 3:* **Gán giá trị cho biến bên trái dấu =** ^ed9e07
- *Step 4:* **Posfix** ^29dfa9

```js
let a = 1
let b = 2
let c = a++ - ++b +1
```

[[#^737316]]$$
\begin{aligned}
Step1: ++b, b = 2 \\
<=> b = b +1 \\
=> b = 3
\end{aligned}
$$
[[#^6ce668]]$$
\begin{aligned}
Step2: a = 1, b = 3 \\
<=> a - b +1 \\
<=> 1 - 3 + 1\\
=> -1
\end{aligned}
$$
[[#^ed9e07]]$$
\begin{aligned}
Step3: c = -1
\end{aligned}
$$
[[#^29dfa9]]$$
\begin{aligned}
Step4: a++, a =1\\
<=> a = a + 1\\
=> a = 2
\end{aligned}
$$



