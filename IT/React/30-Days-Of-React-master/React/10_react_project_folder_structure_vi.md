
<div align="center">
  <h1> 30 Days Of React: React Project Folder Structure</h1>
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

[<< Day 9](../09_Day_Conditional_Rendering/09_conditional_rendering.md) | [Day 11 >>](../11_Day_Events/11_events.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_10.jpg)

- [React Project Folder Structure and File Naming](#react-project-folder-structure-and-file-naming)
  - [File Naming](#file-naming)
  - [Folder](#folder)
  - [Components Folder](#components-folder)
  - [Fragments](#fragments)
- [Exercises](#exercises)
  - [Exercises:Level 1](#exerciseslevel-1)
  - [Exercises:Level 2](#exerciseslevel-2)
  - [Exercises: Level 3](#exercises-level-3)

# React Project Folder Structure and File Naming
Có nhiều cách để sử dụng cấu trúc thư mục hoặc đặt tên tệp tin trong dự án React mà không có cách nào là nghiêm ngặt. Hầu hết thời gian, những lựa chọn này có thể được đưa ra bởi một nhóm. Đôi khi, một công ty có thể đã phát triển các hướng dẫn về những quy ước mã nào cần tuân theo, cấu trúc thư mục và đặt tên tệp tin. Không có cách nào là đúng hay sai để cấu trúc một dự án React, nhưng một số cấu trúc lại tốt hơn những cấu trúc khác về khả năng mở rộng, khả năng bảo trì, dễ dàng làm việc với các tệp tin và cấu trúc dễ hiểu. Nếu bạn muốn tìm hiểu thêm về cấu trúc thư mục, bạn có thể tham khảo các bài viết sau.

- [Cấu trúc Thư mục React bởi
https://www.devaradise.comhttps://www.devaradise.com/react-project-folder-structure)
- [Cấu trúc Thư mục React bởi www.robinwieruch.de ](
https://www.robinwieruch.de/react-folder-structure)
- [Cấu trúc thư mục React bởi Faraz Ahmad](
https://dev.to/farazamiruddin/an-opinionated-guide-to-react-folder-structure-file-naming-1l7i)
- [Cấu trúc Thư mục React bởi
https://maxrozen.com/](https://maxrozen.com/guidelines-improve-react-app-folder-structure/)
Tôi sử dụng một hỗn hợp các quy ước khác nhau. Nếu bạn muốn, bạn có thể tuân theo nó nhưng vui lòng giữ một cấu trúc mà bạn nghĩ ra phù hợp với mình.
## File Naming
Trong tất cả các dự án React của tôi, tôi sẽ sử dụng tên tệp theo kiểu CamelCase cho tất cả các thành phần. Tôi thích sử dụng tên dài và mô tả chi tiết.
## Folder
Tôi đã thấy dễ dàng khi đặt tất cả hình ảnh, biểu tượng và phông chữ vào thư mục assets và tất cả các tệp CSS kiểu vào thư mục styles. Tất cả các thành phần sẽ nằm trong thư mục components.

Cho đến nay, chúng ta đã làm việc với tệp index.js. Chúng ta có rất nhiều thành phần trong tệp index.js. Hôm nay chúng ta sẽ di chuyển tất cả các thành phần vào một tệp duy nhất và chúng ta sẽ nhập tất cả các tệp vào App.js. Trong quá trình này, bạn sẽ thấy cấu trúc thư mục của tôi. Hiện tại chúng ta đang ở thư mục src. Tất cả các thư mục sẽ nằm trong thư mục src. Hãy bắt đầu từ tệp index.js. Ngoài tệp index.js, hãy tạo tệp App.js và di chuyển hầu hết các thành phần chúng ta đã có vào tệp App.js cho thời điểm hiện tại.

Tệp index.js là lối thoát để kết nối thành phần với index.html.
```js
// src/index.js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'

const App = () => <h1>Welcome to 30 Days Of React</h1>

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```
Trong đoạn mã trên, chúng ta có thành phần App. Hãy tạo thành phần App thành một tệp riêng, App.js
```js
// src/App.js
import React from 'react
const App = () => <h1>Welcome to 30 Days Of React</h1>
```
Chúng ta phải xuất component để import nó trong một file khác. Chúng ta có thể xuất nó dưới dạng default hoặc named export. Trong một file, chúng ta có thể tạo một default export và nhiều named exports. Đầu tiên, chúng ta hãy triển khai nó bằng cách sử dụng named export, và sau đó sử dụng default export.

Chúng ta chỉ cần thêm từ khóa `export` trước `let` hoặc `const` để tạo một named export.
```js
// src/App.js
import React from 'react

// named export in arrow function
export const App = () => <h1>Welcome to 30 Days Of React</h1>
```
Xuất khẩu trong một hàm khai báo, một hàm thông thường
```js
// src/App.js
import React from 'react
// named export in regular function, function declaration
export function App () {
return <h1>Welcome to 30 Days Of React</h1>
}
```
Now, let's import the App component from the App.js file to index.js.
```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
import { App } from './App'

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```
Chúng tôi đã thấy một named export và bây giờ hãy triển khai nó với default export. Chúng ta có thể làm điều này theo hai cách nhưng cách tiếp cận được khuyến nghị nếu chúng ta đang xuất các components vì đôi khi chúng ta có thể gán một component với một higher order component khác.
```js
// src/App.js
import React from 'react
// export default in arrow function
export default const App = () => <h1>Welcome to 30 Days Of React</h1>

```


```js
// src/App.js
import React from 'react
// export default in arrow function
export default function App () {
  return <h1>Welcome to 30 Days Of React</h1>
}
```


```js
// src/App.js
// Recommended for most of the cases
import React from 'react
const App = () => <h1>Welcome to 30 Days Of React</h1>
export default App
```
Nếu một thành phần được xuất bản theo mặc định, chúng ta không cần dấu ngoặc nhọn khi nhập.
```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```
Nếu bạn nhớ, chúng ta đã tạo các thành phần sau và đã ráp chúng lại với nhau. Việc làm việc như thế này không dễ chút nào. Bây giờ chúng ta sẽ di chuyển tất cả các thành phần vào một tệp riêng.
```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
import asabenehImage from './images'
import { countriesData } from './data/countries'

// Header component
class Header extends React.Component {
  render() {
    console.log(this.props.data)
    const {
      welcome,
      title,
      subtitle,
      author: { firstName, lastName },
      date,
    } = this.props.data

    return (
      <header>
        <div className='header-wrapper'>
          <h1>{welcome}</h1>
          <h2>{title}</h2>
          <h3>{subtitle}</h3>
          <p>
            {firstName} {lastName}
          </p>
          <small>{date}</small>
        </div>
      </header>
    )
  }
}

const Country = ({
  country: { name, capital, flag, languages, population, currency },
}) => {
  const formatedCapital =
    capital.length > 0 ? (
      <>
        <span>Capital: </span>
        {capital}
      </>
    ) : (
      ''
    )
  const formatLanguage = languages.length > 1 ? `Languages` : `Language`
  return (
    <div className='country'>
      <div className='country_flag'>
        <img src={flag} alt={name} />
      </div>
      <h3 className='country_name'>{name.toUpperCase()}</h3>
      <div class='country_text'>
        <p>{formatedCapital}</p>
        <p>
          <span>{formatLanguage}: </span>
          {languages.join(', ')}
        </p>
        <p>
          <span>Population: </span>
          {population.toLocaleString()}
        </p>
        <p>
          <span>Currency: </span>
          {currency}
        </p>
      </div>
    </div>
  )
}

// User Card Component
const UserCard = () => (
  <div className='user-card'>
    <img src={asabenehImage} alt='asabeneh image' />
    <h2>Asabeneh Yetayeh</h2>
  </div>
)

// Hexadecimal color generator
const hexaColor = () => {
  let str = '0123456789abcdef'
  let color = ''
  for (let i = 0; i < 6; i++) {
    let index = Math.floor(Math.random() * str.length)
    color += str[index]
  }
  return '#' + color
}

const HexaColor = () => <div>{hexaColor()}</div>

const Message = ({ message }) => (
  <div>
    <h1>{message}</h1>
  </div>
)
const Login = () => (
  <div>
    <h3>Please Login</h3>
  </div>
)
const Welcome = (props) => (
  <div>
    <h1>Welcome to 30 Days Of React</h1>
  </div>
)

// A button component
const Button = ({ text, onClick, style }) => (
  <button style={style} onClick={onClick}>
    {text}
  </button>
)

// TechList Component
// class base component
class TechList extends React.Component {
  render() {
    const { techs } = this.props
    const techsFormatted = techs.map((tech) => <li key={tech}>{tech}</li>)
    return techsFormatted
  }
}

// Main Component
// Class Component
class Main extends React.Component {
  render() {
    const {
      techs,
      greetPeople,
      handleTime,
      loggedIn,
      handleLogin,
      message,
    } = this.props
    console.log(message)

    const status = loggedIn ? <Welcome /> : <Login />
    return (
      <main>
        <div className='main-wrapper'>
          <p>Prerequisite to get started react.js:</p>
          <ul>
            <TechList techs={this.props.techs} />
          </ul>
          {techs.length === 3 && (
            <p>You have all the prerequisite courses to get started React</p>
          )}
          <div>
            <Button
              text='Show Time'
              onClick={handleTime}
              style={buttonStyles}
            />{' '}
            <Button
              text='Greet People'
              onClick={greetPeople}
              style={buttonStyles}
            />
            {!loggedIn && <p>Please login to access more information about 30 Days Of React challenge</p>}
          </div>
          <div style={{ margin: 30 }}>
            <Button
              text={loggedIn ? 'Logout' : 'Login'}
              style={buttonStyles}
              onClick={handleLogin}
            />
            <br />
            {status}
          </div>
          <Message message={message} />
        </div>
      </main>
    )
  }
}

// CSS styles in JavaScript Object
const buttonStyles = {
  backgroundColor: '#61dbfb',
  padding: 10,
  border: 'none',
  borderRadius: 5,
  margin: 3,
  cursor: 'pointer',
  fontSize: 22,
  color: 'white',
  margin: '0 auto',
}

// Footer Component
// Class component
class Footer extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <footer>
        <div className='footer-wrapper'>
          <p>Copyright {this.props.date.getFullYear()}</p>
        </div>
      </footer>
    )
  }
}

class App extends React.Component {
  state = {
    loggedIn: false,
    techs: ['HTML', 'CSS', 'JS'],
    message: 'Click show time or Greet people to change me',
  }
  handleLogin = () => {
    this.setState({
      loggedIn: !this.state.loggedIn,
    })
  }
  showDate = (time) => {
    const months = [
      'January',
      'February',
      'March',
      'April',
      'May',
      'June',
      'July',
      'August',
      'September',
      'October',
      'November',
      'December',
    ]

    const month = months[time.getMonth()].slice(0, 3)
    const year = time.getFullYear()
    const date = time.getDate()
    return `${month} ${date}, ${year}`
  }
  handleTime = () => {
    let message = this.showDate(new Date())
    this.setState({ message })
  }
  greetPeople = () => {
    let message = 'Welcome to 30 Days Of React Challenge, 2020'
    this.setState({ message })
  }

  render() {
    const data = {
      welcome: '30 Days Of React',
      title: 'Getting Started React',
      subtitle: 'JavaScript Library',
      author: {
        firstName: 'Asabeneh',
        lastName: 'Yetayeh',
      },
      date: 'Oct 9, 2020',
    }
    const techs = ['HTML', 'CSS', 'JavaScript']

    return (
      <div className='app'>
        {this.state.backgroundColor}
        <Header data={data} />

        <Main
          techs={techs}
          handleTime={this.handleTime}
          greetPeople={this.greetPeople}
          loggedIn={this.state.loggedIn}
          handleLogin={this.handleLogin}
          message={this.state.message}
        />

        <Footer date={new Date()} />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```


## Components Folder
Trong thư mục src sẽ thu thập tất cả các thành phần
```sh
src
  App.js
  index.js
  components
   -auth
    -Signup.js
    -Signin.js
    -Forgotpassword.js
    -Resetpassord.js
  header
   -Header.js
  footer
   -Footer.js
  assets
   -images
   -icnons
   - fonts
  styles
   -button.js
   -button.scss
 utils
  -random-id.js
  -display-time.js
  -generate-color.js
 shared
  -Button.js
  -InputField.js
  -TextAreaField.js
```

Let's create components directory inside src and inside components let's create header director. Create Header.js inside the header directory.
```js
// src/components/header/Header.js
import React from 'react'

const Header = (props) => {
  return (
    <header>
      <div className='header-wrapper'>
        <h1>{welcome}</h1>
        <h2>{title}</h2>
        <h3>{subtitle}</h3>
        <p>
          {firstName} {lastName}
        </p>
        <small>{date}</small>
      </div>
    </header>
  )
}

export default Header
```
Tương tự như Header, hãy di chuyển tất cả các thành phần vào các tệp tin tương ứng.
Tất cả các tệp CSS trên index.html sẽ được chuyển vào thư mục styles và sau đó mỗi phần được chia sẽ được chuyển vào tệp riêng. Hãy thử kiểm tra thư mục styles.
## Fragments
Fragments là một cách để tránh các phần tử cha không cần thiết trong JSX. Chúng ta hãy triển khai một fragment. Chúng ta nhập fragment từ mô-đun react. Như bạn thấy bên dưới, chúng ta nhập React và fragment cùng nhau bằng cách sử dụng dấu phẩy để phân tách.
```js
import React, { Fragment } from 'react'

const Skills = () => {
  return (
    <Fragment>
      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>
    </Fragment>
  )
}
const RequiredSkills = () => {
  return (
    <ul>
      <Skills />
    </ul>
  )
}
```
It is also possível to just extract the fragment module from React as shown below.
```js
import React from 'react'

const Skills = () => {
  return (
    <React.Fragment>
      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>
    </React.Fragment>
  )
}

const RequiredSkills = () => {
  return (
    <ul>
      <Skills />
    </ul>
  )
}
```
In latest version của Reacts, cũng có thể viết mà không cần trích xuất hoặc import bằng các ký hiệu này(<> </>).
```js
import React from 'react'

// Recommended
const Skills = () => {
  return (
    <>
      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>
    </>
  )
}

const RequiredSkills = () => {
  return (
    <ul>
      <Skills />
    </ul>
  )
}
```
Khi chúng ta tạo một thành phần dựa trên lớp, chúng ta đã sử dụng React.Component, chúng ta có thể chỉ nhập thành phần và mã sẽ trông gọn gàng hơn. Hãy xem một ví dụ.
```js
import React from 'react'

// without importing the Component
// Not recommended
class App extends React.Component {
  render() {
    return <h1> 30 Days of React </h1>
  }
}
```


```js
import React, { Component } from 'react'

// This is recommended
class App extends Component {
  render() {
    return <h1> 30 Days of React </h1>
  }
}
```
Hoàn thành tốt. Hãy dành thời gian để thực hiện một số bài tập để rèn luyện trí óc và cơ bắp.
# Exercises

## Exercises:Level 1

1. What is the importance of React Folder Structure and File Naming
2. How do you export file
3. How do you  import file
4. Make a component of module and export it as named or default export
5. Make a component or module and import it
6. Change all the components you have to different folder structure

## Exercises:Level 2

1. Make a simple portfolio using the components we have created so far. Implement a dark mode by using the function we wrote on day 8 challenge.

## Exercises: Level 3

Coming

🎉 CONGRATULATIONS ! 🎉

[<< Day 9](../09_Day_Conditional_Rendering/09_conditional_rendering.md) | [Day 11 >>](../11_Day_Events/11_events.md)
