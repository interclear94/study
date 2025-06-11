# axios

> Promise 기반의 HTTP 클라이언트 라이브러리로, 브라우저와 Node.js 환경에서 모두 사용할 수 있다. 주로 API 서버와 통신할 때 사용되며 fetch보다 더 간편한 기능과 에러 처리가 가능

**기본 특징**

- Promise 기반 (async/await 지원)
- 요청/응답 인터셉터 지원
- 요청 취소, 타임아웃, 응답 데이터 자동 JSON 파싱
- CSRF 보호, withCredentials로 쿠키 전송 가능
- 인스턴스(axios.create)로 공통설정 가능

기본 사용법

```js
import axios from "axios";

// GET 요청
axios
  .get("https://api.example.com/users")
  .then((res) => console.log(res.data))
  .catch((err) => console.error(err));

// POST 요청
axios.post("https://api.example.com/login", {
  email: "test@example.com",
  password: "1234",
});
```

async/await 예시

```js
const getData = async () => {
  try {
    const res = await axios.get("https://api.example.com/data");
    console.log(res.data);
  } catch (error) {
    console.error(error);
  }
};
```

주요 옵션
method : get post put delete 등
url : 요청할 주소
data : post/put 요청시 보낼 데이터
params : get 요청시 커ㅜ리 파라미터
headers : 요청 헤더 설정
timeout : 요청 제한 시간
withCredentials: 쿠키포함 여부 설정

## axios 인스턴스

1. 인스턴스 정의

```ts
const api = axios.creaet({
  baseURL: "https://api.example.com",
  withCredentials: true, // 필요시 작성
});

// GET
api.get("/users").then((res) => console.log(res.data));

// POST
api.post("/login", {
  email: "test@example.com",
  password: "1234",
});
```
