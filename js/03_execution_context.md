# 실행 컨텕스트

> scope, hoisting, this, function, closure 등의 동작원리를 담고 있는 자바스크립트 핵심 원리

실행에 필요한 여러가지 정보

1. 변수 : 전역변수, 지역변ㅅ, 매개변수, 객체의 프로퍼티
2. 함수 선언
3. 변수의 유효범위 (Scope)
4. this

이와 같이 실행에 필요한 정보를 형상화하고 구분하기 위해 자바스크립트 엔진은 실행 컨텍스트를 물리적 객체의 형태로 관리한다.

```js
let x = "xxx";

function foo() {
  let y = "yyy";

  function bar() {
    let z = "zzz";
    console.log(x + y + z);
  }
  bar();
}
foo();
```

스택에 쌓임
global EC -> foo() EC -> bar() EC -> foo EC -> global EC

## 실행 컨텍스트의 3가지 객체

- 실행 컨텍스트는 실행 가능한 코드를 형상화하고 구분하는 추상적인 개념, 물리적으로는 `객체의 형태`를 가지며 아래의 3가지 프로퍼티 소유

Variable Object, Scope chain, this Value

- 변수
- 매개변수와 인수 정보
- 함수 선언(함수 표현식은 제외)

### 전역 컨텍스트의 경우

> 전역객체 (Global Object / GO)
> VO - foo Function Object (전역함수), x ('xxx') 전역 변수 x

### 함수 컨텍스트의 경우

> Variable Object는 Activation Object(AO / 활성 객체)를 가리키며 매개변수와 인수들의 정보를 배열의 형태로 담고 있는 argument객체 추가

VO -> AO arguments {} arguments 객체, bar Function Object 내부 함수, y 'yyy' 지역변수 y

### 함수 변수

1. 선언 단계
   변수 객체(Variable Object) 에 변수를 등록. 이 변수 객체는 스코프가 참조할 수 있는 대상

2. 초기화 단계
   변수 객체에 등록된 변수를 메모리에 할당한다. 이 단계에서 변수는 undefined로 초기화

3. 할당 단계
   undefined로 초기화 된 변수에 실제 값 할당

### 렉시컬 스코프 / 클로저 차이

1. 렉시컬 스코프 (Lexical Scope)
   `정의`
   > 함수가 어디서 작성(정의) 되었느지를 기준으로,
   > **외부 변수에 접근할 수 있는 범위(스코프)**가 결정되는 것

```js
function outer() {
  const name = "jaka";
  function inner() {
    console.log(name);
  }
  inner();
}
outer();
```

- inner()는 name이라는 변수를 **정의 위치 기준(렉시컬)**으로 접근함.
- 실행이 아니라 정의 위치 기준이기 때문에 "렉시컬(Lexical)"이라고 불림

2. 클로저 (Closure)
   `정의`
   > 함수가 자기 외부에 있는 변수에 접근할 수 있는 기능
   > 그리고 그 변수를 **함수가 호출된 이후에도** 유지하는 현상

```js
function makeCounter() {
  let count = 0;
  return function () {
    count++; // 외부 변수에 접근
    return count;
  };
}
```

🔎 비유로 이해하면
• 렉시컬 스코프는 출입증: “너는 여기에 접근할 수 있어”
• 클로저는 자물쇠: “지금 함수가 끝났어도 이 변수는 내가 가지고 있을게”
