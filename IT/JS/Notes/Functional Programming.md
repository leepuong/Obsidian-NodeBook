---
tags:
  - JS
---
##### **ForEach()**
- **Lặp qua từng phần tử trong mảng.**
```js
const callback = (item, i, arr) => {}
array.forEach(callback)
```
##### **Map()**
- **Tạo *mảng mới* dựa trên mảng cũ.**
```js
const countries = ['Finland', 'Estonia', 'Sweden', 'Norway']
//item, i, arr
const newCountries = countries.map((country) => country.toUpperCase())

console.log(newCountries) // ["FINLAND", "ESTONIA", "SWEDEN", "NORWAY"]
```
##### **Filter()**
- **Lọc phần tử theo điều kiện → trả về mảng mới.**
```js
const countries = ['Finland', 'Estonia', 'Sweden', 'Norway', 'Iceland']
//item, i, arr
const countriesWithLand = countries.filter((country) =>
  country.includes('land')
)
console.log(countriesWithLand) // ["Finland", "Iceland"]
```
##### **Reduce()**
- **Gom mảng thành một giá trị duy nhất (sum, object, array mới…)**
```js
const numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
//accumulator, currentValue, index, array
const sum = numbers.reduce((acc, cur) => acc + cur)
console.log(sum) // 55
```
##### **Find()**
- **Tìm phần tử đầu tiên thỏa điều kiện.**
```js
const countries = ['Finland', 'Estonia', 'Sweden', 'Norway', 'Iceland']
//item, i, arr
const sixCharsCountry = countries.find((country) => country.length === 6)
console.log(sixCharsCountry) // Sweden
```
##### **FindIndex()**
- **Trả về *index* của phần tử đầu tiên thỏa điều kiện.**
```js
const countries = ['Finland', 'Estonia', 'Sweden', 'Norway', 'Iceland']
const index = countries.findIndex((country) => country.length === 6)
console.log(index) //2
```
##### **Some()**
- **Kiểm tra *có ít nhất 1 phần tử* thỏa điều kiện không.**
```js
const evens = [0, 2, 4, 6, 8, 10]
const someAreEvens = evens.some((n) => n % 2 === 0)
const someAreOdds = evens.some((n) => n % 2 !== 0)
console.log(someAreEvens) // true
console.log(someAreOdds) // false
```
##### **Every()**
- **Kiểm tra *tất cả phần tử* có thỏa điều kiện không.**
```js
const numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
const allAreEvens = numbers.every((n) => n % 2 === 0)
const allAreOdd s= numbers.every((n) => n % 2 !== 0)

console.log(allAreEven) // false
console.log(allAreOdd)  // false
```