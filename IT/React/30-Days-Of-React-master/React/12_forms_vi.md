
<div align="center">
  <h1> 30 Days Of React: Forms</h1>
  <a class="header-badge" target="_blank" href="https://www.linkedin.com/in/asabeneh/">
  <img src="https://img.shields.io/badge/style--5eba00.svg?label=LinkedIn&logo=linkedin&style=social">
  </a>
  <a class="header-badge" target="_blank" href="https://twitter.com/Asabeneh">
  <img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/asabeneh?style=social">
  </a>

<sub>Author:
<a href="https://www.linkedin.com/in/asabeneh/" target="_blank">Asabeneh Yetayeh</a><br>
<small> October, 2020</small>
</sub>

</div>

[<< Day 11](../11_Day_Events/11_events.md) | [Day 13 >>](../13_Day_Controlled_Versus_Uncontrolled_Input/13_uncontrolled_input.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_12.jpg)

- [Forms](#forms)
  - [Getting data from an input field](#getting-data-from-an-input-field)
  - [Getting multiple input data from form](#getting-multiple-input-data-from-form)
  - [Get data from different input field types](#get-data-from-different-input-field-types)
  - [Form Validation](#form-validation)
  - [What is validation?](#what-is-validation)
  - [What is the purpose of validation](#what-is-the-purpose-of-validation)
  - [Validation Types](#validation-types)
- [Exercises](#exercises)
  - [Exercises: Level 1](#exercises-level-1)
  - [Exercises: Level 2](#exercises-level-2)
  - [Exercises: Level 3](#exercises-level-3)

# Forms
Form được sử dụng để thu thập dữ liệu từ người dùng. Thỉnh thoảng chúng ta sử dụng form để điền thông tin của mình trên giấy hoặc trên trang web. Để đăng ký, đăng nhập hoặc ứng tuyển vào một công việc, chúng ta điền các trường dữ liệu khác nhau để gửi dữ liệu đến cơ sở dữ liệu từ xa. Chúng ta gặp phải các trường dữ liệu khác nhau khi điền vào một form như văn bản đơn giản, email, mật khẩu, điện thoại, ngày tháng, hộp kiểm, nút trình chọn, lựa chọn tùy chọn và trường văn tự. Hiện tại, HTML5 đã cung cấp rất nhiều loại trường. Bạn có thể xem xét các loại trường HTML5 có sẵn sau đây.
```html
<input type="text" />
<input type="number" />
<input type="range" />

<input type="email" />
<input type="password" />
<input type="tel" />

<input type="checkbox" />
<input type="radio" />

<input type="color" />

<input type="url" />
<input type="image" />
<input type="file" />

<input type="hidden" />

<input type="date" />
<input type="datetime-local" />
<input type="month" />
<input type="week" />
<input type="time" />

<input type="reset" />
<input type="search" />
<input type="submit" />
<input type="button" />
```
Các trường HTML khác để lấy dữ liệu từ biểu mẫu là textarea và select với các tùy chọn.
```html
<textarea>Please write your comment ...</textarea>

<select name="country">
  <option value="">Select your country</option>
  <option value="finland">Finland</option>
  <option value="sweden">Sweden</option>
  <option value="denmark">Denmark</option>
  <option value="norway">Norway</option>
  <option value="iceland">Iceland</option>
</select>
```
Ngày hôm nay, chúng ta đã biết hầu hết các trường dữ liệu cần thiết để lấy từ một biểu mẫu. Chúng ta hãy bắt đầu với một trường đầu vào có kiểu văn bản. Trong ngày hôm qua, chúng ta đã thấy các loại sự kiện khác nhau và hôm nay chúng ta sẽ tập trung vào kiểu sự kiện _onChange_ nào sẽ kích hoạt bất cứ khi nào dữ liệu trong trường đầu vào thay đổi. Trường đầu vào có bộ nhớ mặc định để lưu trữ dữ liệu đầu vào, nhưng trong phần này chúng ta sẽ kiểm soát điều đó bằng trạng thái và chúng ta sẽ triển khai một trường đầu vào được kiểm soát. Hôm nay chúng ta sẽ triển khai một trường đầu vào được kiểm soát. Chúng ta sẽ đề cập đến trường đầu vào không được kiểm soát trong một phần khác.
## Getting data from an input field
So far chúng ta chưa nhận được bất kỳ dữ liệu nào từ trường nhập liệu. Bây giờ là lúc để học cách lấy dữ liệu từ một trường nhập liệu. Chúng ta cần một trường nhập liệu, trình nghe sự kiện (onChange), và trạng thái để lấy dữ liệu từ một trường nhập liệu được kiểm soát. Xem ví dụ bên dưới. Phần tử h1 nằm dưới thẻ input hiển thị những gì chúng ta viết vào input. Kiểm tra trực tuyến [demo](
https://codepen.io/Asabeneh/full/OJVpyqm).
The input phần tử có nhiều thuộc tính như giá trị, tên, ID, placeholder, kiểu và trình xử lý sự kiện. Ngoài ra, chúng ta có thể liên kết một nhãn và một trường nhập liệu bằng ID của trường nhập liệu và htmlFor của nhãn. Nếu nhãn và trường nhập liệu được liên kết, nó sẽ tập trung vào trường nhập liệu khi nhấp vào nhãn. Hãy xem ví dụ bên dưới.
```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

class App extends Component {
  // declaring state
  // initial state
  state = {
    firstName: '',
  }
  handleChange = (e) => {
    const value = e.target.value
    this.setState({ firstName: value })
  }

  render() {
    /*
     accessing the state value and 
     this value will injected to the input in the value attribute
     */

    const firstName = this.state.firstName
    return (
      <div className='App'>
        <label htmlFor='firstName'>First Name: </label>
        <input
          type='text'
          id='firstName'
          name='firstName'
          placeholder='First Name'
          value={firstName}
          onChange={this.handleChange}
        />
        <h1>{this.state.firstName}</h1>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```
Chúng ta thường sử dụng form để xử lý thông tin người dùng. Hãy chuyển sang phần form và sử dụng phần tử form.
## Getting multiple input data from form
Trong phần này chúng ta sẽ phát triển một biểu mẫu nhỏ để thu thập thông tin người dùng. Người dùng của chúng ta là một sinh viên. Chúng ta sử dụng một biểu mẫu cha và một số lượng các phần tử đầu vào để thu thập thông tin người dùng. Ngoài ra chúng ta sẽ có trình nghe sự kiện cho biểu mẫu (onSubmit) và cho các phần tử đầu vào (onChange). Xem ví dụ sau để tìm hiểu thêm. Bạn cũng có thể kiểm tra phiên bản trực tuyến [demo](
https://codepen.io/Asabeneh/full/eYNvJda).


```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'
class App extends Component {
  // declaring initial state
  state = {
    firstName: '',
    lastName: '',
    country: '',
    title: '',
  }
  handleChange = (e) => {
    /*
    we can get the name and value like this: e.target.name, e.target.value
    but we can also destructure  name and value from e.target
    const name = e.target.name
    const value = e.target.value
    */
    const { name, value } = e.target
    // [variablename] to use a variable name as a key in an object
    // name refers to the name attribute of the input elements
    this.setState({ [name]: value })
  }
  handleSubmit = (e) => {
    /* 
     e.preventDefault()
      stops the default behavior of form element
     specifically refreshing of page
     */
    e.preventDefault()

    /*
     the is the place where we connect backend api 
     to send the data to the database
     */

    console.log(this.state)
  }

  render() {
    // accessing the state value by destrutcturing the state
    const { firstName, lastName, title, country } = this.state
    return (
      <div className='App'>
        <h3>Add Student</h3>
        <form onSubmit={this.handleSubmit}>
          <div>
            <input
              type='text'
              name='firstName'
              placeholder='First Name'
              value={firstName}
              onChange={this.handleChange}
            />
          </div>
          <div>
            <input
              type='text'
              name='lastName'
              placeholder='Last Name'
              value={lastName}
              onChange={this.handleChange}
            />
          </div>
          <div>
            <input
              type='text'
              name='country'
              placeholder='Country'
              value={country}
              onChange={this.handleChange}
            />
          </div>
          <div>
            <input
              type='text'
              name='title'
              placeholder='Title'
              value={title}
              onChange={this.handleChange}
            />
          </div>

          <button class='btn btn-success'>Submit</button>
        </form>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```
The above form handles only text types but do have different input field types. Let's do another form which handle all the different input field types.
## Get data from different input field types


```js
// index.js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

const options = [
  {
    value: '',
    label: '-- Select Country--',
  },
  {
    value: 'Finland',
    label: 'Finland',
  },
  {
    value: 'Sweden',
    label: 'Sweden',
  },
  {
    value: 'Norway',
    label: 'Norway',
  },
  {
    value: 'Denmark',
    label: 'Denmark',
  },
]

// mapping the options to list(array) of JSX options

const selectOptions = options.map(({ value, label }) => (
  <option value={value}> {label}</option>
))

class App extends React.Component {
  // declaring state
  state = {
    firstName: '',
    lastName: '',
    email: '',
    country: '',
    tel: '',
    dateOfBirth: '',
    favoriteColor: '',
    weight: '',
    gender: '',
    file: '',
    bio: '',
    skills: {
      html: false,
      css: false,
      javascript: false,
    },
  }
  handleChange = (e) => {
    /*
     we can get the name and value like: e.target.name, e.target.value
    Wwe can also destructure name and value from e.target
    const name = e.target.name
    const value = e.target.value
    */
    const { name, value, type, checked } = e.target
    /*
    [variablename] we can make a value stored in a certain variable could be a key for an object, in this case a key for the state
    */

    if (type === 'checkbox') {
      this.setState({
        skills: { ...this.state.skills, [name]: checked },
      })
    } else if (type === 'file') {
      console.log(type, 'cehck here')
      this.setState({ [name]: e.target.files[0] })
    } else {
      this.setState({ [name]: value })
    }
  }
  handleSubmit = (e) => {
    /*
     e.preventDefault()
     stops the default behavior of form element
     specifically refreshing of page
    */
    e.preventDefault()
    const {
      firstName,
      lastName,
      email,
      tel,
      dateOfBirth,
      favoriteColor,
      weight,
      country,
      gender,
      bio,
      file,
      skills,
    } = this.state

    const formattedSkills = []
    for (const key in skills) {
      console.log(key)
      if (skills[key]) {
        formattedSkills.push(key.toUpperCase())
      }
    }
    const data = {
      firstName,
      lastName,
      email,
      tel,
      dateOfBirth,
      favoriteColor,
      weight,
      country,
      gender,
      bio,
      file,
      skills: formattedSkills,
    }
    /*
     the is the place where we connect backend api 
     to send the data to the database
     */
    console.log(data)
  }

  render() {
    // accessing the state value by destrutcturing the state
    const {
      firstName,
      lastName,
      email,
      tel,
      dateOfBirth,
      favoriteColor,
      weight,
      country,
      gender,
      bio,
    } = this.state
    return (
      <div className='App'>
        <h3>Add Student</h3>
        <form onSubmit={this.handleSubmit}>
          <div className='row'>
            <div className='form-group'>
              <label htmlFor='firstName'>First Name </label>
              <input
                type='text'
                name='firstName'
                value={firstName}
                onChange={this.handleChange}
                placeholder='First Name'
              />
            </div>
            <div className='form-group'>
              <label htmlFor='lastName'>Last Name </label>
              <input
                type='text'
                name='lastName'
                value={this.state.lastName}
                onChange={this.handleChange}
                placeholder='Last Name'
              />
            </div>
            <div className='form-group'>
              <label htmlFor='email'>Email </label>
              <input
                type='email'
                name='email'
                value={email}
                onChange={this.handleChange}
                placeholder='Email'
              />
            </div>
          </div>

          <div className='form-group'>
            <label htmlFor='tel'>Telephone </label>
            <input
              type='tel'
              name='tel'
              value={tel}
              onChange={this.handleChange}
              placeholder='Tel'
            />
          </div>

          <div className='form-group'>
            <label htmlFor='dateOfBirth'>Date of birth </label>
            <input
              type='date'
              name='dateOfBirth'
              value={dateOfBirth}
              onChange={this.handleChange}
              placeholder='Date of Birth'
            />
          </div>
          <div className='form-group'>
            <label htmlFor='favoriteColor'>Favorite Color</label>
            <input
              type='color'
              id='color'
              name='color'
              value={favoriteColor}
              onChange={this.handleChange}
              placeholder='Favorite Color'
            />
          </div>
          <div className='form-group'>
            <label htmlFor='weight'>Weight </label>
            <input
              type='number'
              id='weight'
              name='weight'
              value={weight}
              onChange={this.handleChange}
              placeholder='Weight in Kg'
            />
          </div>
          <div>
            <label htmlFor='country'>Country</label> <br />
            <select name='country' onChange={this.handleChange} id='country'>
              {selectOptions}
            </select>
          </div>

          <div>
            <p>Gender</p>
            <div>
              <input
                type='radio'
                id='female'
                name='gender'
                value='Female'
                onChange={this.handleChange}
                checked={gender === 'Female'}
              />
              <label htmlFor='female'>Female</label>
            </div>
            <div>
              <input
                id='male'
                type='radio'
                name='gender'
                value='Male'
                onChange={this.handleChange}
                checked={gender === 'Male'}
              />
              <label htmlFor='male'>Male</label>
            </div>
            <div>
              <input
                id='other'
                type='radio'
                name='gender'
                value='Other'
                onChange={this.handleChange}
                checked={gender === 'Other'}
              />
              <label htmlFor='other'>Other</label>
            </div>
          </div>

          <div>
            <p>Select your skills</p>
            <div>
              <input
                type='checkbox'
                id='html'
                name='html'
                onChange={this.handleChange}
              />
              <label htmlFor='html'>HTML</label>
            </div>
            <div>
              <input
                type='checkbox'
                id='css'
                name='css'
                onChange={this.handleChange}
              />
              <label htmlFor='css'>CSS</label>
            </div>
            <div>
              <input
                type='checkbox'
                id='javascript'
                name='javascript'
                onChange={this.handleChange}
              />
              <label htmlFor='javascript'>JavaScript</label>
            </div>
          </div>
          <div>
            <label htmlFor='bio'>Bio</label> <br />
            <textarea
              id='bio'
              name='bio'
              value={bio}
              onChange={this.handleChange}
              cols='120'
              rows='10'
              placeholder='Write about yourself ...'
            />
          </div>

          <div>
            <input type='file' name='file' onChange={this.handleChange} />
          </div>
          <div>
            <button>Submit</button>
          </div>
        </form>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```


## Form Validation


## What is validation?
Thực hành hoặc quy trình kiểm tra hoặc chứng minh tính hợp lệ hoặc chính xác của điều gì đó trong trường hợp này là dữ liệu.
## What is the purpose of validation
Mục đích chính của việc xác thực là để nhận được dữ liệu mong muốn từ người dùng. Ngoài ra, để ngăn chặn người dùng độc hại và dữ liệu.
## Validation Types
Kiểm tra tính hợp lệ có thể được thực hiện ở phía máy khách hoặc phía máy chủ. Hiện tại, chúng ta đang sử dụng React, một công nghệ giao diện trước, và chúng ta sử dụng kiểm tra tính hợp lệ ở phía máy khách. Một kiểm tra tính hợp lệ có thể được thực hiện bằng cách sử dụng HTML5 tích hợp sẵn hoặc bằng JavaScript (sử dụng biểu thức chính quy).

Trong đoạn mã sau, một kiểm tra tính hợp lệ đã được triển khai cho trường đầu tiên. Hãy cố gắng hiểu cách nó hoạt động. Sự kiện onBlur đã được sử dụng để kiểm tra tính hợp lệ khi đầu vào không được tập trung.
```js
// index.js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

const options = [
  {
    value: '',
    label: '-- Select Country--',
  },
  {
    value: 'Finland',
    label: 'Finland',
  },
  {
    value: 'Sweden',
    label: 'Sweden',
  },
  {
    value: 'Norway',
    label: 'Norway',
  },
  {
    value: 'Denmark',
    label: 'Denmark',
  },
]

// mapping the options to list(array) of JSX options

const selectOptions = options.map(({ value, label }) => (
  <option value={value}> {label}</option>
))

class App extends Component {
  // declaring state
  state = {
    firstName: '',
    lastName: '',
    email: '',
    country: '',
    tel: '',
    dateOfBirth: '',
    favoriteColor: '',
    weight: '',
    gender: '',
    file: '',
    bio: '',
    skills: {
      html: false,
      css: false,
      javascript: false,
    },
    touched: {
      firstName: false,
      lastName: false,
    },
  }
  handleChange = (e) => {
    /*
     we can get the name and value like: e.target.name, e.target.value
    Wwe can also destructure name and value from e.target
    const name = e.target.name
    const value = e.target.value
    */
    const { name, value, type, checked } = e.target
    /*
    [variablename] we can make a value stored in a certain variable could be a key for an object, in this case a key for the state
    */

    if (type === 'checkbox') {
      this.setState({
        skills: { ...this.state.skills, [name]: checked },
      })
    } else if (type === 'file') {
      this.setState({ [name]: e.target.files[0] })
    } else {
      this.setState({ [name]: value })
    }
  }
  handleBlur = (e) => {
    const { name, value } = e.target
    this.setState({ touched: { ...this.state.touched, [name]: true } })
  }
  validate = () => {
    // Object to collect error feedback and to display on the form
    const errors = {
      firstName: '',
    }

    if (
      (this.state.touched.firstName && this.state.firstName.length < 3) ||
      (this.state.touched.firstName && this.state.firstName.length > 12)
    ) {
      errors.firstName = 'First name must be between 2 and 12'
    }
    return errors
  }
  handleSubmit = (e) => {
    /*
      e.preventDefault()
      stops the default behavior of form element 
      specifically refreshing of page
      */
    e.preventDefault()

    const {
      firstName,
      lastName,
      email,
      country,
      gender,
      tel,
      dateOfBirth,
      favoriteColor,
      weight,
      bio,
      file,
      skills,
    } = this.state

    const formattedSkills = []
    for (const key in skills) {
      console.log(key)
      if (skills[key]) {
        formattedSkills.push(key.toUpperCase())
      }
    }
    const data = {
      firstName,
      lastName,
      email,
      country,
      gender,
      tel,
      dateOfBirth,
      favoriteColor,
      weight,
      bio,
      file,
      skills: formattedSkills,
    }
    /*
     the is the place where we connect backend api
      to send the data to the database
      */
    console.log(data)
  }

  render() {
    // accessing the state value by destrutcturing the state
    // the noValidate attribute on the form is to stop the HTML5 built-in validation

    const { firstName } = this.validate()
    return (
      <div className='App'>
        <h3>Add Student</h3>
        <form onSubmit={this.handleSubmit} noValidate>
          <div className='row'>
            <div className='form-group'>
              <label htmlFor='firstName'>First Name </label>
              <input
                type='text'
                name='firstName'
                value={this.state.firstName}
                onChange={this.handleChange}
                onBlur={this.handleBlur}
                placeholder='First Name'
              /> <br />
              <small>{firstName}</small>
            </div>
            <div className='form-group'>
              <label htmlFor='lastName'>Last Name </label>
              <input
                type='text'
                name='lastName'
                value={this.state.lastName}
                onChange={this.handleChange}
                placeholder='Last Name'
              />
            </div>
            <div className='form-group'>
              <label htmlFor='email'>Email </label>
              <input
                type='email'
                name='email'
                value={this.state.email}
                onChange={this.handleChange}
                placeholder='Email'
              />
            </div>
          </div>

          <div className='form-group'>
            <label htmlFor='tel'>Telephone </label>
            <input
              type='tel'
              name='tel'
              value={this.state.tel}
              onChange={this.handleChange}
              placeholder='Tel'
            />
          </div>

          <div className='form-group'>
            <label htmlFor='dateOfBirth'>Date of birth </label>
            <input
              type='date'
              name='dateOfBirth'
              value={this.state.dateOfBirth}
              onChange={this.handleChange}
              placeholder='Date of Birth'
            />
          </div>
          <div className='form-group'>
            <label htmlFor='favoriteColor'>Favorite Color</label>
            <input
              type='color'
              id='favoriteColor'
              name='favoriteColor'
              value={this.state.favoriteColor}
              onChange={this.handleChange}
              placeholder='Favorite Color'
            />
          </div>
          <div className='form-group'>
            <label htmlFor='weight'>Weight </label>
            <input
              type='number'
              id='weight'
              name='weight'
              value={this.state.weight}
              onChange={this.handleChange}
              placeholder='Weight in Kg'
            />
          </div>
          <div>
            <label htmlFor='country'>Country</label> <br />
            <select name='country' onChange={this.handleChange} id='country'>
              {selectOptions}
            </select>
          </div>

          <div>
            <p>Gender</p>
            <div>
              <input
                type='radio'
                id='female'
                name='gender'
                value='Female'
                onChange={this.handleChange}
                checked={this.state.gender === 'Female'}
              />
              <label htmlFor='female'>Female</label>
            </div>
            <div>
              <input
                id='male'
                type='radio'
                name='gender'
                value='Male'
                onChange={this.handleChange}
                checked={this.state.gender === 'Male'}
              />
              <label htmlFor='male'>Male</label>
            </div>
            <div>
              <input
                id='other'
                type='radio'
                name='gender'
                value='Other'
                onChange={this.handleChange}
                checked={this.state.gender === 'Other'}
              />
              <label htmlFor='other'>Other</label>
            </div>
          </div>

          <div>
            <p>Select your skills</p>
            <div>
              <input
                type='checkbox'
                id='html'
                name='html'
                onChange={this.handleChange}
              />
              <label htmlFor='html'>HTML</label>
            </div>
            <div>
              <input
                type='checkbox'
                id='css'
                name='css'
                onChange={this.handleChange}
              />
              <label htmlFor='css'>CSS</label>
            </div>
            <div>
              <input
                type='checkbox'
                id='javascript'
                name='javascript'
                onChange={this.handleChange}
              />
              <label htmlFor='javascript'>JavaScript</label>
            </div>
          </div>
          <div>
            <label htmlFor='bio'>Bio</label> <br />
            <textarea
              id='bio'
              name='bio'
              value={this.state.bio}
              onChange={this.handleChange}
              cols='120'
              rows='10'
              placeholder='Write about yourself ...'
            />
          </div>

          <div>
            <input type='file' name='file' onChange={this.handleChange} />
          </div>
          <div>
            <button>Submit</button>
          </div>
        </form>
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```


# Exercises

## Exercises: Level 1

1. What is the importance of form?
2. How many input types do you know?
3. Mention at least four attributes of an input element
4. What is the importance of htmlFor?
5. Write an input type which is not given in the example if there is?
6. What is a controlled input?
7. What do you need to write a controlled input?
8. What event type do you use to listen changes on an input field?
9. What is the value of a checked checkbox?
10. When do you use onChange, onBlur, onSubmit?
11. What is the purpose of writing e.preventDefault() inside the submit handler method?
12. How do you bind data in React? The first input field example is data binding in React.
13. What is validation?
14. What is the event type you use to listen when an input changes?
15. What are event types do you use to validate an input?

## Exercises: Level 2

1. Validate the form given above (a gif image or a video will be provided later). First try to validate without using any library then try it with [validator.js](https://www.npmjs.com/package/validator).

## Exercises: Level 3

Coming ..

🎉 CONGRATULATIONS ! 🎉

[<< Day 11](../11_Day_Events/11_events.md) | [Day 13 >>](../13_Day_Controlled_Versus_Uncontrolled_Input/13_uncontrolled_input.md)
