## 스코프: 변수의 유효 범위

```js
function outer() {
  let a = 1;
  function inner() {
    console.log(a); // 접근 가능
  }
}
```

## 클로저

> 함수가 외부 변수에 접근할 수 있는 상태를 기억하는 것

```js
function makeCounter() {
  let count = 0;
  return function () {
    count++;
    return count;
  };
}

const counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

## 비동기 / 이벤트 루프

구조 분해, 스프레드, 옵셔널 체이닝

```js
const user = { name: "jaka" };
// 구조분해
const { name } = user;

// 스프레드
const newUser = { ...user, email: "jaka@example." };

// 옵셔널 체이닝
console.log(user?.address.zip);
```
