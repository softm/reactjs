### # React Document
  - https://reactjs.org/docs/react-api.html
  - https://react.vlpt.us/basic/
  - chorme plugin : https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc/related
  - vscode extentions : Smart Semicolon

### # Install node
  - NodeJs
  - ```node -v```
  - ```npm -v```

#### # Install wsl2 (Optional)
  - https://docs.microsoft.com/ko-kr/windows/wsl/install-win10  

### # Install yarn
  - ```npm install --global yarn```
  - ```yarn --version```

### # Install npx
  - ```npm install npx -g```
  - ```npm install -g npm \\ To upgrade```

### # Install VSC
  - https://code.visualstudio.com/download

### # Install git
  - https://git-scm.com
  - ```git --version```

### # Learn js, html , css ...
  - http://vanilla-js.com/
  - arra, const, let, object
  - node : pacakage.json

### # React
  - Made by Facebook 
  - [Install React Developer Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi/related?hl=ko)
  - [Pacakge React](https://www.npmjs.com/package/react)

### # View js statistic
  - https://stateofjs.com/
    - https://2020.stateofjs.com/en-US/technologies/front-end-frameworks/

### # Create React App ( CRA )
  - https://github.com/facebook/create-react-app
  - ```npx create-react-app my-app```
  - ```cd my-app```  
  - ```code .```

### # Create Git
  - ```git init```
  - ```git remote add origin "https://github.com/softm/react_myapp.git"```
  - ```git add .```
  - ```git commit -m "init"```
  - ```git config --global user.email "softm@nate.com"```
  - ```git config --global user.name "jihoon.kim"```
  - ```git push origin master```

### # React JS Fundamentals Course (2019 Update!)
```javascript
"scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build"
  }
```
  - ```npm start```
  - ```http://localhost:3000/```

### # Modify App.js
```javascript
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div>
        <h1>test~~~</h1>
    </div>
  );
}

export default App;
```

### # Add Component - JSX ( Javascript & XML )
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import Test from './Test';
import reportWebVitals from './reportWebVitals';

ReactDOM.render(
  <React.StrictMode>
    <div>
      <App />
      <Test />
    </div>
  </React.StrictMode>,
  document.getElementById('root')
);

```

### # Props
```js
function Test2(props) {
  console.log(props);
  return <div>
   <h5>Test2</h5>
    <pre>
    props.param : {props.param}<br/>
    props.something : {props.something}<br/>
    props.papapa : {props.papapa[0]}<br/>
    </pre>
  </div>;
}

function Test3({param, something, papapa}) {
  console.log(param, something, papapa);
  return <div>
  <h5>Test3</h5>
   <pre>
    param : {param}<br/>
    something : {something}<br/>
    papapa : {papapa[0]}<br/>
   </pre>
  </div>;
}

ReactDOM.render(
  <React.StrictMode>
    <div>
      <App />
      <Test />
      <Test2 param="test" something={true} papapa={["he"]}/>
      <Test3 param="test" something={true} papapa={["he"]}/>
      {
        list
      }
    </div>
  </React.StrictMode>,
  document.getElementById('root')
);
```
### # Loop For Map - 1
```js
const list = [
  {
    name:"item1",
    title:"아이템1"
  },
  {
    name:"item2",
    title:"아이템2"
  },
  {
    name:"item3",
    title:"아이템3"
  }
];

ReactDOM.render(
  <React.StrictMode>
    <div>
      <App />
      <Test />
      <Test2 param="test" something={true} papapa={["he"]}/>
      <Test3 param="test" something={true} papapa={["he"]}/>
      <h1># Loop Test</h1>
      {
        list.map(item=> (
          <Test3 param={item.name} something={true} papapa={["he"]}/>
        ))
      }
    </div>
  </React.StrictMode>,
  document.getElementById('root')
);
```

### # Loop For Map - 2 : Function
function fRender(item){
  return <Test3 param={item.title}/>;
}
ReactDOM.render(
  <React.StrictMode>
    <div>
      <App />
      <h1># Loop Test</h1>
      {
        list.map(fRender)
      }
    </div>
  </React.StrictMode>,
  document.getElementById('root')
);


### # Loop For Map - 3 : index.js:1 Warning: Each child in a list should have a unique "key" prop.
```js
const list = [
  {
    id:1,
    name:"item1",
    title:"아이템1"
  },
  {
    id:2,
    name:"item2",
    title:"아이템2"
  },
  {
    id:3,
    name:"item3",
    title:"아이템3"
  }
];

function fRender(item){
  return <Test3 key={item.id} param={item.title}/>;
}
ReactDOM.render(
  <React.StrictMode>
    <div>
      <App />
      <h1># Loop Test</h1>
      {
        list.map(fRender)
      }
    </div>
  </React.StrictMode>,
  document.getElementById('root')
);
```

### # Check props type
  - ```npm i prop-types```
```js
import PropsType, { string } from "prop-types";

function Test3({param, something, papapa}) {
  console.log(param, something, papapa);
  return <div>
    <h5>Test3 {param}</h5>
  </div>;
}

Test3.propTypes={
  param:PropsType.string.isRequired,
  something:PropsType.bool,
  papapa:PropsType.array
}
```

### # State , setState
```js
import logo from './logo.svg';
import './App.css';
import React from 'react';

class App extends React.Component {
  state = {
    count:0
  };
  // setState --> Call render
  add = () =>{
    console.log("add");
    //this.state.count = 1;
    //this.setState({count: this.state.count + 1});
    this.setState(current => ({count: current.count + 1}) );
  };
  
  minus = () =>{
    console.log("minus");
    //this.state.count = -1;    
    // this.setState({count:this.state.count - 1});
    this.setState(current => ({count: current.count - 1}) );    
  };

  render() {
    return ( <div>
      <h1>The number is {this.state.count}</h1>
      <button onClick={this.add}>Add</button>
      <button onClick={this.minus}>Minus</button>
    </div>
    );
  }
}

export default App;
```

### # Life Cycle
  - mount
  - update
  - unmount
  - will -> did
  
```js
import logo from './logo.svg';
import './App.css';
import React from 'react';

class App extends React.Component {
  constructor(props) {
    super(props);
    console.log("constructor");
  }

  componentDidMount(){
    console.log("component did mount");
  }
  
  componentDidUpdate(){
    console.log("component did update");
  }

  componentWillUnmount(){
    console.log("unmount")  
  }
  
  state = {
    count: 0
  };

  // setState --> Call render
  add = () => {
    console.log("add");
    //this.state.count = 1;
    //this.setState({count: this.state.count + 1});
    this.setState(current => ({ count: current.count + 1 }));
  };

  minus = () => {
    console.log("minus");
    //this.state.count = -1;    
    // this.setState({count:this.state.count - 1});
    this.setState(current => ({ count: current.count - 1 }));
  };

  render() {
    console.log("render");
    return (<div>
      <h1>The number is {this.state.count}</h1>
      <button onClick={this.add}>Add</button>
      <button onClick={this.minus}>Minus</button>
    </div>
    );
  }
}

export default App;
```

### # Load setState
```js
import logo from './logo.svg';
import './App.css';
import React from 'react';

class App extends React.Component {
  state = {
    isLoading: true
  };

  componentDidMount(){
    console.log("component did mount");
    setTimeout(() => {
      this.setState({
        isLoading: false
      });
    },6000);
  }

  render() {
    console.log("render");
    const {isLoading} = this.state;
    return (
      <div>{isLoading?"Loading...":"We are ready"}</div>
    );
  }
}

export default App;
```

### # Using axios
  - ```npm i axios```
  -  yts api
    - https://yts.mx/api#list_movies
    - https://yts.mx/
  
```js
import logo from './logo.svg';
import './App.css';
import React from 'react';
import axios from 'axios';

class App extends React.Component {
  state = {
    isLoading: true,
    movies: []
  };

  getMovies = async () => {
    const { data: { data: { movies } } } = await axios.get("https://yts.mx/api/v2/list_movies.json");
    //this.setState({movies:movies});
    this.setState({movies,isLoading : false});    
    console.log(movies);
  }

  componentDidMount() {
    this.getMovies();
  }

  render() {
    console.log("render");
    const { isLoading } = this.state;
    return (
      <div>{isLoading ? "Loading..." : "We are ready"}</div>
    );
  }
}

export default App;

```
### # Render The Movies
#### # Movie
```js
import React from 'react';
import axios from 'axios';
import PropType from "prop-types";

function Movie({id, year, title, summary, poster}){
  return <h4>{title}</h4>
}

Movie.PropType = {
  id:PropType.number.isRequired,
  year:PropType.number.isRequired,
  title:PropType.string.isRequired,
  summary:PropType.string.isRequired,
  poster:PropType.string.isRequired
}

export default Movie;
```
: destructuring assignment
```js
import logo from './logo.svg';
import './App.css';
import React from 'react';
import axios from 'axios';
import Movie from "./Movie";

class App extends React.Component {
  state = {
    isLoading: true,
    movies: []
  };

  getMovies = async () => {
    const { data: { data: { movies } } } = await axios.get("https://yts.mx/api/v2/list_movies.json");
    //this.setState({movies:movies});
    this.setState({ movies, isLoading: false });
    console.log(movies);
  }

  componentDidMount() {
    this.getMovies();
  }

  render() {
    console.log("render");
    const { isLoading, movies } = this.state;
    return (
      <div>{isLoading ? "Loading..." : movies.map(movie => {
        console.log(movie);
        return <Movie key={movie.id} id={movie.id} year={movie.year} title={movie.title} summary={movie.summary} poster={movie.medium_cover_image} />
      })}</div>
    );
  }
}

export default App;
```

### # Adding Genres - Array Key
```js
import React from 'react';
import PropType from "prop-types";
import "./Movie.css";

function Movie({id, year, title, summary, poster,genres}){
  return <div className="movie">
    <img src={poster} alt={title} title={title}/>
    <div className="movie__data">
      <h3 className="movie__title">{title}</h3>
      <h5 className="movie__year">{year}</h5>
      <ul className="genres">
        {genres.map((genre,index) =>(
          <li key={index} className="genres_genre">{genre}</li>
        ))}
      </ul>
      <p className="movie__summary">{summary}</p>
    </div>
  </div>
}

Movie.PropType = {
  id:PropType.number.isRequired,
  year:PropType.number.isRequired,
  title:PropType.string.isRequired,
  summary:PropType.string.isRequired,
  poster:PropType.string.isRequired,
  genres:PropType.arrayOf(PropType.string).isRequired
}

export default Movie;
```

```js
import "./App.css";
import React from "react";
import axios from "axios";
import Movie from "./Movie";

class App extends React.Component {
  state = {
    isLoading: true,
    movies: [],
  };

  getMovies = async () => {
    const {
      data: {
        data: { movies },
      },
    } = await axios.get("https://yts.mx/api/v2/list_movies.json");
    //this.setState({movies:movies});
    this.setState({ movies, isLoading: false });
    console.log(movies);
  };

  componentDidMount() {
    this.getMovies();
  }

  render() {
    console.log("render");
    const { isLoading, movies } = this.state;
    return (
      <section className="container">
        {isLoading ? (
          <div className="loader">
            <span className="loader__text">Loading...</span>
          </div>
        ) : (
            <div className="movies">
              {movies.map((movie) => {
            console.log(movie);
            return (
              <Movie
                key={movie.id}
                id={movie.id}
                year={movie.year}
                title={movie.title}
                summary={movie.summary}
                poster={movie.medium_cover_image}
                genres={movie.genres}
              />
            );
          })}
            </div>
        )}
      </section>
    );
  }
}

export default App;
```

### # Style
```css
body {
  margin: 0px;
  padding: 0px;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  background-color: #eff3f7;
  height: 100%;
  box-sizing: border-box;
}

html,
body,
#potato,
.container {
  height: 100%;
  display: flex;
  justify-content: center;
}

.loader {
  width:100%;
  height:100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.movies {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  padding:50px;
  width: 80%;
}

.movies .movie {
  width : 45%;
  background-color: white;
  margin-bottom: 70px;
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  padding: 20px;
  color: #d2d2e2;
}

.move img {
  position: relative;
  top: -50px;
  max-width: 120px;
  margin-right: 30px;
}

.movie .movie__title,
.movie .movie__year {
  margin: 0;
  font-weight: 300;
}

.movie .movie__title{
  margin-bottom: 5px;
  font-size:24px;
  color: #2c2c2c;
}


.movie .movie__genres {
  list-style: none;
  padding:0;
  display: flex;
  margin: 5px;
}

.movie__genres li {
  margin-right: 10px;
}
```

### # Create github page
  - ```npm i gh-pages```
  - ```npm run depoly```
  - 디렉토리, 레포지터리명 동일해야함.
  - public 레포지터리여야함.

#### : Modify package.json 
    : gh-pages -d build
    : homepage
```js
{
  "name": "my-app",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@testing-library/jest-dom": "^5.11.9",
    "@testing-library/react": "^11.2.5",
    "@testing-library/user-event": "^12.7.3",
    "axios": "^0.21.1",
    "prop-types": "^15.7.2",
    "react": "^17.0.1",
    "react-dom": "^17.0.1",
    "react-scripts": "4.0.3",
    "web-vitals": "^1.1.0"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build"
  },
  "eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest"
    ]
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  },
  "devDependencies": {
    "gh-pages": "^3.1.0"
  },
  "homepage": "https://softm.github.io/my_app"
}
```  

### # react-router-dom
  - ```npm install --save react-router-dom```
  - https://www.npmjs.com/package/react-router-dom
  
```js
import React from "react";
import { BrowserRouter, HashRouter, Route, Link } from "react-router-dom";
import Home from "./routes/Home";
import About from "./routes/About";
import Navigation from "./componets/Navigation";

function App(){
  return <BrowserRouter>2
      <Navigation/>
      <Route path="/" exact={true} component={Home}>
      </Route>
      <Route path="/about" component={About}/>
      <Route path="/movie/:id" component={Detail}/>
  </BrowserRouter>
}

export default App;
```

#### : Navigator.js
```js
import React from "react";
import { Link } from "react-router-dom";

function Navigation(){
    return <div>
        <Link to="/">Home</Link><br/>
        <Link to="/about">About</Link><br/>
    </div>;
}

export default Navigation;

```

#### : Detail.js
```js
import React from "react";

// function Detail({location}){
//     console.log(location);
//     return <span>Detail page</span>;
// }

class Detail extends React.Component {
    componentDidMount(){
        const {location,history} = this.props;
        console.log(this.props);
        
        if ( location.state === undefined ) {
            history.push("/");
        }
    }

    render(){
        
   // const { data: { data: { movies } } } 

        const { location ,match:{params}} = this.props;
        const param = {};
        if ( location.state ) {
            return <>
            <div>id : {params.id}</div>
            <span>{location.state.title}</span>
            </>;
        } else {
            return null;
        }
    }
}

export default Detail;
```