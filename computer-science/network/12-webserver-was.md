# 웹서버 vs WAS

## 웹서버

- 항상 동일한 페이지 (static page) 를 반환한다.
- 소프트웨어와 하드웨어로 구분된다.

### 하드웨어

- 웹서버가 설치되어있는 컴퓨터 혹은 컴퓨팅 서비스

### 소프트웨어

- 브라우저 클라이언트로부터 HTTP 요청을 받아, 정적인 컨텐츠를 제공하는 프로그램

- 따라서, 클라이언트의 요청을 서비스하는 기능을 가진다.

1. 정적인 컨텐츠를 제공한다. (WAS 거치지 않음)
2. 동적인 컨텐츠 제공을 위한 요청을 전닳나다.
   - 클라이언트의 요청을 WAS 에 보내고, WAS 가 처리한 결과를 클라이언트에 응답
   - 여기서 클라이언트는 일반적으로 `웹 브라우저`를 의미한다.

- ex) Nginx

## WAS (Web Application Server)

- 인자의 내용에 맞게 동적인 컨텐츠를 반환한다.
- 웹서버에 의해서 실행되는 프로그램을 통해서 만들어진 결과물을 반환한다.

- ex) Tomcat