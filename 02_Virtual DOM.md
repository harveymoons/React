#### DOM (Document Object Model) 
  
객체로 문서 구조를 표현하는 방법, `XML`이나 `HTML`로 작성  
  
웹 브라우저는 `DOM`을 활용하여 객체에 `자바스크립트`와 `CSS`를 적용  
  
DOM은 `트리 형태`라서 특정 노드를 찾거나 수정하거나 제거하거나 원하는 곳에 삽입할 수 있다  
  
`HTML 마크업`을 시각적인 형태로 변환하는 것은 웹 브라우저가 하는 주 역할  
  
DOM을 조작할 때마다 엔진이 웹 페이지를 새로 그리기 때문에 업데이트가 너무 잦으면 성능이 저하될 수 있다  
  
리액트는 `Virtual DOM` 방식을 사용하여 DOM 업데이트를 `추상화`함으로써 DOM 처리 횟수를 최소화하고 효율적으로 진행  
  
`Virtual DOM` 을 사용하면 실제 DOM에 접근하여 조작하는 대신,  
  
이를 `추상화`한 `자바스크립트 객체`를 구성하여 사용, 마치 `실제 DOM의 가벼운 사본`과 비슷  
  
`Virtual DOM` 이 언제나 제공할 수 있는 것은 `업데이트 처리 간결성`이다
