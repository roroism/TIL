# TODAY I LEARNED

## Learned

### 타입스크립트 - 타입

#### 정적 타입

**정적 타입**
- 변수의 타입이 컴파일시 결정됨
- 타입 에러를 미리 발견해 프로그램의 안정성을 높여줌

**동적 타입**
- 변수 타입이 런타임시에 결정됨
- 개발 과정에는 타입을 신경쓰지 않아도 돼서 편하지만 런타임시에 어떤 문제가 생길지 모른다.

#### 강타입과 약타입

**강타입**
- 서로 다른 타입인 값으로 연산시 컴파일러, 인터프리터에서 에러 발생
- Python, Typescript

**약타입**
- 서로 다른 타입인 값으로 연산시 컴파일러, 인터프리터가 임의적으로 타입을 변환해 연산함
- C++, Java, javascript

#### 타입스크립트의 컴파일

- 다른 언어는 컴파일시 코드를 기계어로 변환하지만 타입스크립트의 컴파일 결과물은 자바스크립트 소스코드이다.
- 타입스크립트는 자바스크립트의 컴파일타임에 런타임 에러를 미리 걸러내기 위한 장치라고 생각하면 된다.
