# react-example

**npm, npx, node.js 필수 설치!**

node.js는 구글에 검색해서 설치. (npm이랑 같이 설치되기때문에 npm은 별도로 설치 안해도 됨)

`node -v`, `npm -v`, `npx -v`으로 버전 확인 가능.

`git --version`으로 깃 버전 확인 가능.

```bash
npm install npx -g # npx를 글로벌로 설치.
```


# creat-react-app
React Web App을 Set up 할 수 있게 도와줌.

```bash
# iterm에서 실행
cd Documents # 내 문서에서

npx creap-react-app project_name # 리액트 설치

npm start # vscode 해당 프로젝트 터미널에서 실행 -> 서버 실행
```

# github에 리포지토리 생성
```bash
# vscode 터미널에서 실행. ~/Documents/project_name/ 확인하고,
git init
```
깃허브로 가서 리포지토리 생성. (packge.json 에 있는 name으로 하는게 편함)

리포지토리 url이 생성되면 

```bash
git remote add origin 리포지토리 url 붙여넣기.

git add

git commit -m 첫번째 커밋 내용

git push origin master
```

그리고 깃헙에서 새로고침하면 리포지토리에 복사되어있음.

# React work
- index.js에 있는 `ReactDOM.render(<App />, document.getElementById("root"));` root에서부터 시작, 이후에 작성한 코드를 html로 밀어넣는다.

- vertual DOM 존재하지않기때문에 빠르다. 처음부터 html을 갖고있는게 아니고 빈 html안에서 html을 추가하거나 삭제하기때문에 빠름.

- component는 html을 반환하는 함수이다. `<conponentName />` 이런식으로 사용. javascript와 html의 조합을 jsx라고 부름.

```javascript
// 컴포넌트의 시작과 끝은 항상
import React from "react";
function App() { // 첫 글자는 대문자
  //...
}
export default App;
// 이런 형식이여야 한다. 그래야 jsx가 component 사용을 이해함.
```

- ! react application 은 한번의 하나의 componant만 rendering 할 수 있음. 모든 컴포넌트는 app.js 안에 들어가야하고 여기엔 많은 컴포넌트를 import할 수 있음.

- 컴포넌트에 정보를 보낼 수 있음! 그리고 얼마든지 재사용 가능한 컴포넌트 만들 수 있음.


### Food component에 value로 prop name 주기
```javascript
<Food fav="kimchi" /> // food component에 fav라는 이름의 property를 kimchi라는 value로 줌.
// property는 여러개일 수 있고 component에 인자로 들어감.

function Food ({ fav }) { // () 안에 props.fav 또는 {}내부에 fav는 property를 가져오는 방법
  return <h1> Like {fav}</h1>; 
}
```

## props types
전달 받은 props가 내가 원하는 props인지 확인 해줌.
```bash
npm install prop-types #설치
```
```javascript
import PropTypes form "prop-types"; // 파일에 import

// 사용법
Food.propTypes = { // 이름은 꼭 propTypes로 지어야 함. 
  name: PropTypes.string.isRequired,
  // ...
  // 모든 자료형을 체크할 수 있고 array, function, object도 가능.
}
```

# dynamic data
## function component
```javascript
function App () {

}
```

## class component
```javascript
class App extends React.Component {
  render() {
    //...
  }
}
```
- `function`이 아니기 떄문에 `return`을 가지고있지 않음.
- react component는 `render` 메소드를 갖고있지만 내가 extend from 을 했기 때문에 나도 `render` 메소드가 있음.

> **function component는 function이고 뭔가를 return해서 screen에 표시됨.**
> **class component는 class임. 하지만 react component로 부터 확장되고 screen에 표시됨. 그리고 표시되는 걸 render 메소드 안에 넣어야 함!**
> **react는 자동적으로 모든 class component의 render 메소드를 실행하고자 함.**


## state
 class component에 있음
```javascript
class App extends React.Component {
  state = {
    count: 0
  };
  renter() {
    return <h1>The number is: {this.state.count}</h1> // The number is: 0, class이기 때문에 이렇게 써야함
  }
}
```

state는 ocject임
컴포넌트의 데이터를 넣을 공간이 있고 이 데이터는 변함. 그래서 state를 사용해야함.
state에 바꾸고 싶은 데이터를 넣을것임
setState 를 호출함으로 새 state(변경된 데이터?) 와 함께 render function이 호출됨…???? 그래서 작업을 이어갈수가 있는거신가..!

setState를 호출할 때 마다 react는 새로운 state와 함께 render function을 호출함
 내가 setState를 호출 할 때만! 일어날 일이야 어썸~ 후우........
 
 state가 필요 없을 경우에는 class component를 쓰지 않아도 됨.
 
> **state와 props의 차이점**
> props (“properties”의 줄임말) 와 state 는 일반 JavaScript 객체입니다. 
> 두 객체 모두 렌더링 결과물에 영향을 주는 정보를 갖고 있는데, 한 가지 중요한 방식에서 차이가 있습니다. 
> props는 (함수 매개변수처럼) 컴포넌트에 전달되는 반면 state는 (함수 내에 선언된 변수처럼) 컴포넌트 안에서 관리됩니다.

## life cycle method
life cycle method 를 가지는데 이건 기본적으로 리액트가 컴포넌트를 생성하고 없애는 방법임.
렌더 전에 호출되는 몇개의 펑션이 있음.

- mounting 태어나는것과 가틈 cunstructor() 클라스 만들때 자바스크립트에서 쓰는거야 컨스트럭트는~~ 컨스트럭트는 렌더 전에 호출됨.
> 컴포넌트가 마운트 될 때, 스크린에 표시될 떄, 나의 웹사이트에 갈 때 컨스트럭트를 호출함 이후에 렌더! 
> componentDidMount는 컴포넌트가 처음 render됐을떄 알려주는건가요??? 마운팅보다 먼저 호출됨.
- updating 일반적인 업데이트
- unmounting 컴포넌트가 죽다. (페이지를 바꿀때)
- render 제일 처음 호출됨.

setState를 호출하면 component를 호출하고 먼저 render를 호출 한 뒤 업데이트가 완료되었다고 말하면 componentDidUpdate가 호출됨.

## axios
axios는 fetch 위에 있는 작은 layer.
뭔가 요청하고있음. 네트워크에 있음..! 
```bash
npm install axios #설치
```
```javascript
import axios from "axios"; // App.js맨 상단에 추가

getMovies = async () => { // axios는 가끔 빠르지않아서 기다려야함. async 함수가 비동기임. 이걸 기다려야함
  const movies - await axios.get("API URL"); // await -> axios를 기다려야함. axios가 끝날 떄 까지 기다렸다가 계속함
};
componentDidMount() {
  this.getMocies();
}
```

# CSS
CSS파일로 작업하는게 좋습니다~
```javascript
// jax에서 태그에 바로 style 적용하는 방법
<div stype={{ color: "red" }}></div>

// 파일 상단에 import
import "./App.css";
```

**jsx는 `class` 대신에 `className`을 써야합니다!**
**`label` 같은 경우 javascript에서 `for`은 loop 이기 때문에 `htmlFor` 을 써야합니다!**

# github 무료 호스팅
[노마드코더 유튜브][https://www.youtube.com/watch?v=HdFbiPkZXR0&list=PL7jH19IHhOLPp990qs8MbSsUlzKcTKuCf&index=23]

