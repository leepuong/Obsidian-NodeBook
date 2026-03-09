
<div align="center">
  <h1> 30 Days Of React: Conditional Rendering</h1>
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

[<< Day 8](../08_Day_States/08_states.md) | [Day 10 >>](../10_React_Project_Folder_Structure/10_react_project_folder_structure.md)

![30 Days of React banner](../images/30_days_of_react_banner_day_9.jpg)

# Conditional Rendering
Như chúng ta có thể hiểu từ thuật ngữ, hiển thị điều kiện là một cách để hiển thị các JSX hoặc thành phần khác nhau ở các điều kiện khác nhau. Chúng ta có thể triển khai hiển thị điều kiện bằng các câu lệnh if và else thông thường, toán tử ba chấm và &&. Hãy triển khai một kiểu hiển thị điều kiện khác.
## Conditional Rendering using If and Else statement
Trong mã bên dưới, chúng ta có trạng thái ban đầu của loggedIn là false. Nếu trạng thái là false chúng ta thông báo người dùng đăng nhập, nếu không chúng ta chào mừng người dùng.
```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'

// class based component
class Header extends React.Component {
  render() {
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
          <p>Select a country for your next holiday</p>
        </div>
      </header>
    )
  }
}

class App extends React.Component {
  state = {
    loggedIn: false,
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

    // conditional rendering using if and else statement

    let status

    if (this.state.loggedIn) {
      status = <h3>Welcome to 30 Days Of React</h3>
    } else {
      status = <h3>Please Login</h3>
    }

    return (
      <div className='app'>
        <Header data={data} />
        {status}
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```
Chúng ta hãy thêm một phương thức cho phép chúng ta chuyển đổi trạng thái của người dùng. Chúng ta nên có một nút để xử lý sự kiện đăng nhập và đăng xuất.
```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'

// A button component
const Button = ({ text, onClick, style }) => (
  <button style={style} onClick={onClick}>
    {text}
  </button>
)

// CSS styles in JavaScript Object
const buttonStyles = {
  backgroundColor: '#61dbfb',
  padding: 10,
  border: 'none',
  borderRadius: 5,
  margin: '3px auto',
  cursor: 'pointer',
  fontSize: 22,
  color: 'white',
}

// class based component
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

class App extends React.Component {
  state = {
    loggedIn: false,
  }
  handleLogin = () => {
    this.setState({
      loggedIn: !this.state.loggedIn,
    })
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

    let status
    let text

    if (this.state.loggedIn) {
      status = <h1>Welcome to 30 Days Of React</h1>
      text = 'Logout'
    } else {
      status = <h3>Please Login</h3>
      text = 'Login'
    }

    return (
      <div className='app'>
        <Header data={data} />
        {status}
        <Button text={text} style={buttonStyles} onClick={this.handleLogin} />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```
How về nếu điều kiện của chúng ta là hơn hai? Giống như JavaScript thuần túy chúng ta có thể sử dụng câu lệnh if else if. Nói chung, hiển thị điều kiện không khác gì câu lệnh điều kiện thuần túy JavaScript.
## Conditional Rendering using Ternary Operator
Ternary operator là một lựa chọn thay thế cho câu lệnh if else. Tuy nhiên, có nhiều trường hợp sử dụng cho ternary operator hơn so với if else statement. Ví dụ, bạn có thể sử dụng ternary operator bên trong styles, className hoặc nhiều nơi trong một component thay vì câu lệnh if else thông thường.
```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'

// A button component
const Button = ({ text, onClick, style }) => (
  <button style={style} onClick={onClick}>
    {text}
  </button>
)

// CSS styles in JavaScript Object
const buttonStyles = {
  backgroundColor: '#61dbfb',
  padding: 10,
  border: 'none',
  borderRadius: 5,
  margin: '3px auto',
  cursor: 'pointer',
  fontSize: 22,
  color: 'white',
}

// class based component
class Header extends React.Component {
  render() {
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

class App extends React.Component {
  state = {
    loggedIn: false,
  }
  handleLogin = () => {
    this.setState({
      loggedIn: !this.state.loggedIn,
    })
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

    let status = this.state.loggedIn ? (
      <h1>Welcome to 30 Days Of React</h1>
    ) : (
      <h3>Please Login</h3>
    )

    return (
      <div className='app'>
        <Header data={data} />
        {status}
        <Button
          text={this.state.loggedIn ? 'Logout' : 'Login'}
          style={buttonStyles}
          onClick={this.handleLogin}
        />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```
Ngoài JSX, chúng ta cũng có thể hiển thị điều kiện một thành phần. Hãy thay đổi JSX điều kiện trên thành một thành phần.
```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'

// A button component
const Button = ({ text, onClick, style }) => (
  <button style={style} onClick={onClick}>
    {text}
  </button>
)

// CSS styles in JavaScript Object
const buttonStyles = {
  backgroundColor: '#61dbfb',
  padding: 10,
  border: 'none',
  borderRadius: 5,
  margin: '3px auto',
  cursor: 'pointer',
  fontSize: 22,
  color: 'white',
}

// class based component
class Header extends React.Component {
  render() {
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

class App extends React.Component {
  state = {
    loggedIn: false,
  }
  handleLogin = () => {
    this.setState({
      loggedIn: !this.state.loggedIn,
    })
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

    const status = this.state.loggedIn ? <Welcome /> : <Login />

    return (
      <div className='app'>
        <Header data={data} />
        {status}
        <Button
          text={this.state.loggedIn ? 'Logout' : 'Login'}
          style={buttonStyles}
          onClick={this.handleLogin}
        />
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```


## Conditional Rendering using && Operator
The && toán tử render phần tử JSX bên phải nếu phần biểu thức bên trái (thành công) là đúng.
```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'

// A button component
const Button = ({ text, onClick, style }) => (
  <button style={style} onClick={onClick}>
    {text}
  </button>
)

// CSS styles in JavaScript Object
const buttonStyles = {
  backgroundColor: '#61dbfb',
  padding: 10,
  border: 'none',
  borderRadius: 5,
  margin: '3px auto',
  cursor: 'pointer',
  fontSize: 22,
  color: 'white',
}

// class based component
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
      <header style={this.props.styles}>
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

class App extends React.Component {
  state = {
    loggedIn: false,
    techs: ['HTML', 'CSS', 'JS'],
  }
  handleLogin = () => {
    this.setState({
      loggedIn: !this.state.loggedIn,
    })
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

    // We can destructure state

    const { loggedIn, techs } = this.state

    const status = loggedIn ? <Welcome /> : <Login />

    return (
      <div className='app'>
        <Header data={data} />
        {status}
        <Button
          text={loggedIn ? 'Logout' : 'Login'}
          style={buttonStyles}
          onClick={this.handleLogin}
        />
        {techs.length === 3 && (
          <p>You have all the prerequisite courses to get started React</p>
        )}
        {!loggedIn && (
          <p>
            Please login to access more information about 30 Days Of React
            challenge
          </p>
        )}
      </div>
    )
  }
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```
Trong phần trước, chúng ta đã sử dụng hộp thoại cảnh báo để chào đón mọi người và cũng để hiển thị thời gian. Hãy hiển thị lời chào và thời gian trên trình duyệt DOM thay vì hiển thị trên hộp thoại cảnh báo.
```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'

// class based component
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
      <header style={this.props.styles}>
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
  margin: '3px auto',
  cursor: 'pointer',
  fontSize: 22,
  color: 'white',
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

    return (
      <div className='app'>
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

## Testimony
Now it is time to express your thoughts about the Author and 30DaysOfReact. You can leave your testimonial on this [link](https://x.com)
https://www.asabeneh.com/testimonials)


## Exercises

### Exercises: Level 1

1. What is conditional rendering?
2. How do you implement conditional rendering?
3. Which method of conditional rendering do you prefer to use?

### Exercises: Level 2

1. Make a single page application which changes the body of the background based on the season of the year(Autumn, Winter, Spring, Summer)
2. Make a single page application which change the body of the background based on the time of the day(Morning, Noon, Evening, Night)

### Exercises: Level 3

1. Fetching data takes some amount of time. A user has to wait until the data get loaded. Implement a loading functionality of a data is not fetched yet. You can simulate the delay using setTimeout.

🎉 CONGRATULATIONS ! 🎉

[<< Day 8](../08_Day_States/08_states.md) | [Day 10 >>](../10_React_Project_Folder_Structure/10_react_project_folder_structure.md)
