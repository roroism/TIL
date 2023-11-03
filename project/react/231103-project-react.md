# TODAY I LEARNED

## Learned

### REST(Representational State Transfer) 등장 배경

- HTTP는 다양한 HTTP 메서드 (GET, POST, PUT, DELETE 등)를 지원한다.
- 실제로는 서버가 HTTP 메서드를 기존 설명에 맞게 사용하지 않더라도, 프로그램 개발은 가능하다.
- 하지만 각 서비스가 서로 다른 방식으로 개발하면, 개발자 사이의 소통에 문제가 발생할 수 있다.
- 따라서 기준이 되는 아키텍처로 REST를 채택할 수 있다.

### REST 이해하기

- REST는 Representational State Transfer의 약자이다.
- 말 그대로 특정한 자원(resource)에 대하여, 자원의 상태에 대한 정보를 주고받는 개발 방식이다.
- REST의 구성 요소는 다음과 같다.
	- 자원(resource) : URI를 이용
	- 행위(verb)	 : HTTP 메서드를 이용
	- 표현(representation) : 페이로드(payload)를 이용

### REST 예제 살펴보기

- REST 방식을 채택한 서버로 요청(request)을 보내는 예시는 다음과 같다.
- 클라이언트가 회원가입을 하고 싶은 상태다.
- 이때, 아이디는 "gildong", 비밀번호는 "1234"로 설정하고 싶다면?

> 자원	 : 회원(user)
> 행위	 : 회원 등록
> 표현	 : 아이디 : "gildong", 비밀번호 : "1234"

> URI : https://www.example.com/users
> HTTP Method : POST
> Payload : {"id" : "gildong", "password" : "1234"}

### REST API

- API (Application Programming Interface) : 프로그램이 상호작용하기 위한 인터페이스
- REST API : REST 아키텍처를 따르는 API
- REST API 호출 : REST 방식을 따르고 있는 서버에 특정한 요청(request)을 전송하는 행위

### REST API 연습하기

- 목킹(mocking) : 어떠한 기능이 있는 것처럼 흉내내어 구현한 것을 의미한다.
- 클라이언트 개발을 위해 간단히 서버 기능을 테스트할 때 사용한다.
- 처음부터 모든 서버 기능을 개발하고, 클라이언트 개발을 시작하면 개발 일정에 지연이 생길 수 있다.

### REST API 목킹 서비스 예시

https://jsonplaceholder.typicode.com/

#### 사용자(user) 정보 API 확인해 보기

1) 전체 사용자 목록

https://jsonplaceholder.typicode.com/users

2) 특정 사용자

https://jsonplaceholder.typicode.com/users/1

