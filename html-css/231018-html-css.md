# TODAY I LEARNED

## Learned

### 웹 접근성 오류 유형 12개 리뷰

#### role="alert"

- 시간에 민감하고 중요한(오류, 제안) 실시간 콘텐츠. 이 부분이 role="status"와 다른점이다.
- 이 요소를 갱신할 때 초점을 받지 않아야 한다.
- aria-live="assertive" 속성과 aria-atomic="true" 속성이 자동 할당된다.
- 긴급하지 않는 부분에는 설정하지 않는다.

```html
<!-- O: 오류 메시지 -->
<p role="alert">우편번호 입력 오류.</p>

<!-- O: 제안 메시지 -->
<p role="alert">로그인 후 이용 가능.</p>
```

#### 실전 ARIA – 상태 (states) : 실무에서 사용했던 ARIA 명세들

```html
<element aria-current="page|step|location|date|time|true|false(default)"> 
<element aria-selected="false|true|undefined(default)"> 
<element aria-haspopup="true|menu|dialog|listbox|tree|grid|false(default)"> 
<element aria-expanded="true|false|undefined(default)"> 
<element aria-hidden="true|false|undefined(default)"> 
<element aria-invalid="true|false(default)|grammar|spelling">
```

#### aria-current

- 현재 맥락과 일치하는 항목을 의미.
- page | step | location | date | time | true | false(default)
- page: 현재 '페이지'와 일치하는 시각적으로 강조한 링크.
- step: 현재 '단계'와 일치하는 시각적으로 강조한 링크.
- 아래는 사이트의 네이게이션에 사용한 예시.

```html
<!-- O: 현재 페이지 링크 -->
<nav>
    <h2>글로벌 네비게이션</h2>
    <ul>
        <li><a href="/home" aria-current="page">홈</a></li>
        <li><a href="/ongoing">연재</a></li>
        <li><a href="/ranking">랭킹</a></li>
    </ul>
</nav>

<!-- O: 현재 단계 링크 -->
<nav>
    <h2>회원 가입</h2>
    <ol>
        <li><a href="/accept-terms" aria-current="step">약관 동의</a></li>
        <li><a href="/id-password">아이디/비밀번호 생성</a></li>
        <li><a href="/email-authentication">이메일 인증</a></li>
    </ol>
</nav>
```

- 홈이라는 페이지에서 네이게이션의 홈이라는 링크는 현재 페이지의 링크라는 것을 나타내 준다.

#### aria-selected

- false | true | undefined(default)
- 단일 또는 다중 선택이 가능한 요소(role="gridcell | option | row | tab")에 선택 상태를 명시하는 의미.
- role="tab" 요소에 가장 흔히 사용.
- 보통 a태그나 button에 적용한다. tab 이외의 요소에는 잘 사용하지는 않는다.
- 키보드 초점을 받을 수 있는 요소에 적용.
- undefined(default): 속성 또는 값을 선언하지 않은 경우 초기값. 선택할 수 없음.
- true: 선택 가능한 요소를 선택했음.
- false: 선택 가능한 요소를 선택하지 않았음.

```html
<!-- O: role="tab" 요소에 선택 상태를 명시 -->
<div role="tablist">
  <a id="mon-anchor" href="#mon" role="tab" aria-selected="true">월</a>
  <a id="tue-anchor" href="#tue" role="tab" aria-selected="false">화</a>
</div>
```

- aria-selected 속성을 사용하면 css로 스타일링을 하는데에도 도움을 받을 수 있다. 예를 들어 aria-selected의 값이 true인 요소만 선택해서 스타일링을 다르게 입히는 기법을 적용할 수가 있다.

#### aria-haspopup

- true | menu | dialog | listbox | tree | grid | false(default)
- a나 button 요소에 적용하게 된다.
- 눌렀을 때 팝업이나 submenu가 뜬다면, 그런 것들을 가지고 있다라는 정보를 전달해주는 용도이다.
- 요소에 연결되어 있는 팝업(메뉴, 대화상자 등) 정보를 제공.
- 팝업 유형은 menu, listbox, tree, grid, dialog 으로 제한.
- 일반적으로 menu와 dialog 유형이 빈번.

```html
<!-- O: aria-haspopup="menu|true" -->
<button type="button" id="menu-button" aria-haspopup="menu" aria-controls="menu-list" aria-expanded="false">메뉴</button>
<ul id="menu-list" role="menu" aria-labelledby="menu-button" hidden>
    <li>
        <a href="/completed">완결</a>
    </li>
    ...
</ul>

<!-- O: aria-haspopup="dialog"-->
<a href="#login-dialog" aria-haspopup="dialog">로그인</a>
<section id="login-dialog" role="dialog" aria-labelledby="login-heading" aria-modal="true" hidden>
    <h2 id="login-heading">로그인</h2>
    ...
</section>
```

