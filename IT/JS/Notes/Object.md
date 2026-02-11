---
tags:
  - JS
---
##### Tạo **Object** 
- **An empty object**
```js
const person = {}
```
- **An objecting with values **
```js
const rectangle = {
  length: 20,
  width: 20,
}
```

```js
console.log(rectangle) // {length: 20, width: 20}
```

```js
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js',
  ],
  isMarried: true,
}
```

```js
console.log(person) //{firstName: 'Asabeneh', lastName: 'Yetayeh', age: 250, country: 'Finland', city: 'Helsinki', …}
```
  

##### Get value from an **Object** 
- **Using .**
```js
console.log(person.age);
```
- **Using square bracket and a quote**
```js
console.log(person["firstName"]);
```


##### **Object** Methods 
- **_Object.assign:_** Copy **object** mà không thay đổi object cũ
```js
const copyPerson = Object.assign({}, person)
console.log(copyPerson)
```
- **_Object.keys_:** Lấy **key** hoặc **property** thành mảng
```js
//tạo thành mảng chứa key
const keys = Object.keys(copyPerson)
console.log(keys) //['name', 'age', 'country', 'skills', 'address', 'getPersonInfo']

//tạo thành mảng chứa property
const address = Object.keys(copyPerson.address)
console.log(address) //['street', 'pobox', 'city']
```
- **_Object.values_:** Lấy **value** thành mảng
```js
const values = Object.values(copyPerson)
console.log(values)
```
- **_Object.values_:** Lấy key và value thành mảng
```js
const entries = Object.entries(copyPerson)
console.log(entries)
//['firstName', 'Asabeneh']
//['lastName', 'Yetayeh']
//['age', 250]
//['country', 'Finland']
//['city', 'Helsinki']
//['skills', Array(10)]
//['getFullName', ƒ]
//['nationality', 'Ethiopian']
//['title', 'teacher']
//['isMarried', true]
//['getPersonInfo', ƒ]
```
- **_Object.hasOwnProperty_:** kiểm tra 1 **key** hoặc **property** có tồn tại trong **object** không
```js
console.log(copyPerson.hasOwnProperty('name'))
console.log(copyPerson.hasOwnProperty('score'))
```


