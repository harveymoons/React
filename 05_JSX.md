## JSX란
  
리액트에서 사용되는 자바스크립트 `확장`문법이다  
  
`JSX`는 정식 자바스크립트 문법이 아니다  
  
그렇기 때문에 웹브라우저에서 정상작동하려면 자바스크립트 문법으로 변환해줘야 한다  
  
`JSX`는 `import` 라는 문법을 사용하여 외부에서 파일을 불러온다  
  
이 또한 자바스크립트 문법으로 변화해줘야 웹브라우저에서 정상작동한다  
  
이러한 `JSX`문법을 변환해줄 때 `웹팩`과 `바벨`이라는 도구를 사용한다  
  
브라우저가 실행되기 전에 코드가 `번들링`되는 과정에서 바벨을 사용하여 일반 자바스크립트 형태의 코드로 변환된다  
  
`JSX`는 코드로 보면 `XML` 형식이지만 실제로는 `자바스크립트 객체`이다  
  
---  
  
###### 웹팩

`번들러` 도구로서 불러온 파일들을 모두 합쳐서 하나의 파일로 생성한다  
  
###### 바벨  
  
정식 자바스크립트 문법이 아닌 표현들을 정식 자바스크립트 문법에 입각한 코드 형태로 변환한다  
  
---  
  
## JSX 문법  
  
컴포넌트에 여러 요소가 있다면 반드시 부모 요소 하나로 감싸야 한다  
```jsx
import React from 'react';

function App(){
  return(
    <h1>Hello React!</h1>
    <h2>Do you work well?</h2>
  )
}
```  
  
위와 같은 경우 여러개의 요소를 하나의 부모의 요소로 감싸지 않아서 에러가 발생한다  
  
아래와 같이 수정하게되면 정상작동한다  
  
```jsx
import React from 'react';

function App(){
  return(
    <div>
      <h1>Hello React!</h1>
      <h2>Do you work well?</h2>
    </div>
  )
}
```  
  
### 리액트 컴포넌트에서 요소 여러 개를 하나의 요소로 꼭 감싸 줘야하는 이유  
  
`Virtual DOM`에서 컴포넌트 변화를 감지해 낼 때 효율적으로 비교할 수 있도록  
  
컴포넌트 내부는 `하나의 DOM 트리 구조`로 이루어져야 한다는 규칙이 있기 때문  
  
### 자바스크립트 표현식  
  
자바스크립트 표현식을 작성하려면 `JSX` 내부에서 코드를 `{ }`로 감싸야 한다  
  
```jsx
import React from 'react';

let name = 'React';

function App(){
  return(
    <div>
      <h1>Hello {name}!</h1>
      <h2>Do you work well?</h2>
    </div>
  )
}
```  
### `JSX` 내부에서는 `조건부 연산자`만 사용할 수 있다
  
`JSX` 내부의 자바스크립트 표현식`{ }`에서 `if`문을 사용할 수 없다  
  
자바스크립트 표현식 내부에서는 `조건부 연산자`만 사용할 수 있다  
  
`조건부 연산자`의 종류로는 `삼항연산자`, `AND 연산자(&&)`, `OR 연산자(||)` 등이 있다  
  
```jsx
import React from 'react';

let name = 'React';

function App(){
  return <div>{name === 'React' && <h1>I'm React~</h1>}</div>
}
```  
  
`조건부 연산자`로 렌더링을 할 수 있는 이유는 리액트에서 `false`를 렌더링할 때는  
  
`null`과 마찬가지로 아무것도 나타나지 않기 때문이다  
  
주로 `JSX`를 여러 줄로 작성할 때 괄호`( )`로 감싸고, 한 줄로 표현할 수 있는 `JSX`는 감싸지 않는다  
  
`리액트 컴포넌트`에서는 함수에서 `undefined`만 반환하여 렌더링하는 상황을 만들면 안된다  
  
```jsx
import React from 'react';

let name = undefined;

function App(){
  return name;
}

export default App;
```  
  
위와 같은 코드는 에러가 발생한다  
  
```jsx
import React from 'react';

let name = undefined;

function App(){
  return name || 'This value is undefined';
}

export default App;
```   
  
위와 같이 `OR 연산자(||)`를 사용하여 해당 값이 `undefined`일 때 사용할 값을 지정하여 오류를 방지할 수 있다  
  
반면 JSX 내부에서 `undefined`를 `렌더링`하는 것은 괜찮다  
  
```jsx
import React from 'react';

let name = undefined;

function App(){
  return <div>{name}</div>;
}

export default App;
```  
  
## 인라인 스타일링  
  
리액트에서 DOM 요소에 스타일을 적용할 때는 문자열 형태로 넣는 것이 아니라 `객체 형태`로 넣어 주어야 한다  
  
스타일 이름중에 background-color처럼 `-`문자가 포함되는 이름일 경우  
  
`-`문자를 없애고 `카멜표기법`으로 작성해야 한다  
  
`background-color` --> `backgroundColor`  
  
```jsx
import React from 'react';

let name = 'React';
const style = {
  backgroundColor: 'lightblue';
  color: white;
  width: 100%;
  height: 92px;
};

function App(){
  return <div style={style} >{name}</div>;
}

export default App;
```  
  
### `class` 대신 `className` 사용  
  
`JSX`에서 `class` 속성을 사용하려면 `className` 속성을 사용해야 합니다  
  
###### css  
  
```css
.react {
  background: lightblue;
  color: white;
  font-size: 48px;
  font-weight: bold;
  padding: 16px;
}
```
  
###### jsx  
  
```jsx
import React from 'react';
import './App.css';

let name = undefined;

function App(){
  return <div className='react'>{name}</div>;
}

export default App;
```  
  
## `JSX`에서는 `태그`를 꼭 닫아야 한다  
  
`HTML`에서는 `태그`를 닫지 않고 코드를 작성하기도 한다  
  
아래와 같이 작성해도 에러가 발생하지 않는다  
  
```html
<input>
<hr>
<br>
```  
  
이러한 `태그`를 `self-closing 태그`라고 부른다  
  
하지만 `JSX`에서는 `태그`를 닫아주지 않으면 에러가 발생한다  
  
`JSX`에서는 아래와 같이 태그를 닫아주어야 한다  
  
```jsx
import React from 'react';

function App(){
  return (
    <div>
      <input></input> 또는 <input />
      <hr></hr> 또는 <hr />
      <br></br> 또는 <br />
    </div>
  )
}

export default App;
```  
  
## 주석  
  
`JSX`에서 주석은 `{/* ... */}` 이러한 형태로 사용한다  
  
