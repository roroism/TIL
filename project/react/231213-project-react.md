# TODAY I LEARNED

## Learned

### React Router 소개

- React 어플리케이션에서 페이지/컴포넌트 내비게이션 (i.e. 페이지 라우팅; page routing)을 위해 쓰이는 표준 라이브러리.
- URL에 따른 UI (User Interface)를 동기화하여 일정한 경험을 제공.

> 페이지 라우팅; Page routing - 주어진 요청(URL)에 따라 해당 URL을 어떤 handler에서 처리하고 어떤 페이지를 렌더링 할 지 결정하는 과정

#### React-router가 하는 일

> History Stack
> 브라우저의 히스토리 스택. 웹 브라우저는 스택에 사용자가 방문해왔던 링크를 차곡차곡 저장한다.

- History 스택을 관리
- URL과 routes 경로를 매칭
- Route 매칭을 통해 적절한 UI를 렌더링

#### 예시로 이해하기

##### Route 선언

- `BrowserRouter` - React app과 브라우저의 URL을 연결해서 매칭되는 URL에 따라 어떤 컴포넌트를 렌더링 할 지 정하겠다는 선언
- `Route` - URL이 해당 `path`에 매칭될 경우 해당 `element`를 렌더링하겠다는 선언
    - `Route`를 중첩으로 선언할 경우 중첩된 `path`로 URL 매칭. 위 예시 중 option 1의 경우 /groups/:guid가 최종 `path`
    - `path`의  `:guid`는 URL param의 name을 의미 (i.e. `:guid -> params.guid`). 예를 들어, URL이 /groups/3일 경우, guid param에는 3이 할당될 것

##### Link를 이용한 내비게이션

- `Link`를 사용함으로써 전체 페이지를 새로고침 할 필요 없이 URL을 바꿔줄 수 있다 (반응 속도가 빨라지는 효과!)
- `Link`가 클릭 될 경우 browser stack에 해당 로케이션을 쌓음

##### JS 코드를 이용한 내비게이션

- `useNavigate()` - method call로 페이지 내비게이션을 할 수 있는 함수를 리턴
- `navigate(path: string)` - 주어진 `path`로 리다이렉트. History stack에 해당 location을 push
- `navigate(path: string, { replace: true })` - 주어진 `path`로 URL을 바꿔치기. History stack에 해당 location을 push하지 않고 대체 하는 것
- `navigate(delta: number)` - History stack에서 top에서  `delta` 만큼 밑에 있는 location로 리다이렉트 하고, 해당 location을 history stack에 push
    - e.g. `navigate(-1)` = “페이지 뒤로 가기”와 비슷

##### URL Param 읽기

- URL Parameter는 URL에서 `/`로 분리되는 segment (e.g. /groups/**234** ➡️ 234가 URL param)
- 컴포넌트 안에서 `useParams()`를 호출하면 parameter map이 리턴된다.
- 이 map을 이용하여 param value를 읽을 수 있다.

##### Search Param 읽고 쓰기

- URL에서 `?`뒤에 붙여지는 query string 의미 (e.g. /groups?**sort_key=created_at**)
- 컴포넌트 안에서 `useSearchParams()`를 호출하면 parameter map이 리턴된다.
    - React Router가 search parameter를 읽고 조작하기 쉽게 만들어줌! 사용법이 React의 `useState()`와 비슷하다.
    - URL의 search params 객체는 `useState()`와 비슷하게 state로 관리된다. 따라서, `setSearchParams({ sortKey: 'new_key'})`를 호출할 경우 URL의 search param도 업데이트가 된다 (e.g. /groups?**sort_key=new_key**)

