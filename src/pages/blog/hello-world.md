---
title: This is My Very First Post - Hello World!
date: 2018-12-29
---

![](https://i1.theportalwiki.net/img/thumb/b/b8/PortalBoxart.jpg/250px-PortalBoxart.jpg)

# Portals

Portals는 리액트에서 컴포넌트를 렌더링할 때, 부모 컴포넌트의 바깥에 렌더링 할 수 있게 해주는 기능이다.
일반적으로 포탈이 "어딘가로 향하는 문"이라는 개념으로 사용되는 것을 알면 이 기능에 대해 이해하기가 쉽다.

리액트에서는 컴포넌트를 렌더링할 때, children은 부모컴포넌트의 DOM 내부에 렌더링된다.  
그러나 Portals를 사용하면 DOM 계층 구조 바깥에 있는 DOM 노드로 자식을 렌더링할 수 있다.

```jsx
ReactDOM.createPortal(element, 배치할 DOM 식별자);
```

두번째 인자로 받는 Dom에 첫번째 인자로 받은 컴포넌트를 렌더링한다는 의미이다.

간단한 예제로 사용법을 살펴보자.

# 사용해보기

react를 사용해본 사람이라면 많이 보았을 index.html의 내부이다.  
여기에 `portals`라는 id를 가진 div태그 하나를 추가한다.  
이 portals라는 id를 가진 div 태그는 포탈의 종착지가 되며 div태그 안에 element를 렌더링한다는 의미다.

```html
<html lang="ko">
  <head> </head>
  <body>
    <div id="root"></div>
    <div id="portals"></div>
  </body>
</html>
```

`App.js`의 내부 코드.  
Portal이라는 컴포넌트를 만들어서 id로 DOM에 접근한 뒤 포탈로 children을 이동시킨다.

```jsx
import React from "react"
import ReactDOM from "react-dom"

const Portal = ({ children }) => {
  const portals = document.getElementById("portals")
  return ReactDOM.createPortal(children, portals)
}

export default function App() {
  return (
    <div>
      <Portal>portals 로 이동됨!</Portal>
    </div>
  )
}
```

이 코드는 다음과 같은 과정을 거친다.

1. `<Portal />` 컴포넌트가 감싸고 있는 요소는 `<Portal />`의 children이 되고
2. id가 `portals`인 element의 DOM에 접근해 렌더링이 된다.

그러나 여기서 의문점이 생긴다.  
index.html 의 root 가 아닌 다른 곳에 렌더링이 되는데 state를 사용할 수 있을까? 🤔

# Portal을 통한 이벤트 버블링

앞서 했던 질문에 대한 답변을 하자면, **결론적으로 portal인지 아닌지에 상관없이 다른 React의 자식요소와 같게 동작한다.** DOM 트리에서의 위치에 상관없이 portal은 여전히 React 트리에 존재하기 때문이다.

코드를 다음처럼 바꿔보면 훨씬 이해하기 쉽다.

```jsx
import React, { useState } from "react"
import ReactDOM from "react-dom"

const Portal = ({ children }) => {
  const portals = document.getElementById("portals")
  return ReactDOM.createPortal(children, portals)
}

export default function App() {
  const [count, setCount] = useState(0)

  return (
    <div>
      <div>{count}</div>
      <Portal>
        <button onClick={() => setCount(count + 1)}>add</button>
      </Portal>
    </div>
  )
}
```

버튼을 누르면 count가 올라가고, count를 화면에 출력하는 간단한 코드이다.

![](https://images.velog.io/images/nsunny0908/post/cbfe9215-a0bd-40cc-a229-1489f7dd0b17/Aug-22-2021%2001-12-44.gif)

Portal과 count를 출력하는 div는 다른 위치에 있는데도 잘 동작하는 것을 볼 수 있다.
이런식으로 portals을 활용해서 DOM 계층 구조 바깥에 있는 DOM 노드로 자식을 렌더링하는것이 가능하다.  
컴포넌트 렌더링을 원하는 DOM에 자유롭게 할 수 있고 root에 적용되어있는 기본 css를 무시하고 컴포넌트를 만들고 싶을때 꽤 유용할 것 같다.
​
