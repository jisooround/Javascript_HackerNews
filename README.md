# Javascript_HackerNews Client App

김민태 강사님의 강의를 보고 실습한 Javascript_Hacker News Client App 프로젝트입니다.

### 💟 사용 API

Hacker News RESTful API<br />

> RESTful API란?<br /> > [출처](https://aws.amazon.com/ko/what-is/restful-api/)

### 💟 사용스택

Javascript, HTML5, Tailwind <br />

### 💟 새롭게 알게된 내용

#### ajax request & response

`ajax.open("GET", "URL", 동기처리여부(boolean))`으로 요청하고 `ajax.send()`, `JSON.parse(ajax.response)`로 응답

#### hash change 이벤트리스너 동작시키기

해시값이 클릭때마다 변한다면 `location.hash` 로 현재 해시값을 가져올 수 있다.<br/>
해시 기호를 떼고 싶다면 `substring()`을 사용하면 된다.
`location.hash.substring(1)`

#### 임시 DOM을 활용하여 가독성있게 HTML 구조 다루기

변경 전 코드
`
for (let i = 0; i < 10; i++) {
const li = document.createElement("li");
const a = document.createElement("a");

a.href = `#${newsFeed[i].id}`;
a.innerHTML = `<li>${newsFeed[i].title}</li> (${newsFeed[i].comments_count})`;

li.appendChild(a);
ul.appendChild(li);
}`

변경 후 코드
`for (let i = 0; i < 10; i++) {
const div = document.createElement("div");

div.innerHTML = `

  <li>
    <a href="#${newsFeed[i].id}">
      ${newsFeed[i].title} (${newsFeed[i].comments_count})
    </a> 
  </li>`;

ul.appendChild(div.children[0]);
}`
div 구조를 임시로 만들어서 html 구조를 그대로 넣었고 실제로는 div의 children[0]만 넣어서 원래 구조를 유지<br/>
div.children[0] 대신 div.firstElementChild 를 사용할 수 있다.
