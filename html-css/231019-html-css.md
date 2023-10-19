# TODAY I LEARNED

## Learned

### 웹 접근성 오류 유형 12개 리뷰

#### aria-expanded

- true | false | undefined(default)
- a나 button 요소에 보통 적용을 한다.
- aria-controls 속성을 이용하여 제어 대상을 명시.
- 툴팁(role="tooltip"), 알럿(role="alert"), 알럿 대화상자(role="alertdialog"), 대화상자(role="dialog")와 같이 동적으로 표시 상태를 결정(토글)하는 요소에 사용.
- true: 요소 또는 제어 대상 확장 상태.
- false: 요소 또는 제어 대상 축소 상태.

```html
<!-- O: 어코디언 -->
<dt>
    <button type="button" aria-controls="answer-99" aria-expanded="false">보너스 코인은 언제 소진되나요?</button>
</dt>
<dd id="answer-99" hidden>
    <p>만료기한이 짧은 보너스 코인이 일반 코인보다 먼저 소진됩니다.</p>
</dd>

<!-- O: 팝업 -->
<a id="popular-btn" href="#popular" aria-haspopup="menu" aria-expanded="false">인기</a>
<ul id="popular" role="menu" aria-labelledby="popular-btn" hidden>
    <li><a href="#romance">로맨스</a></li>
    ...
</ul>
```

- 예시로 아코디언 ui 같은 경우에 탭과 해당하는 내용이 닫혀 있는 경우 탭에 aria-expanded="false"를 적용한다.

#### aria-hidden

- true | false |  undefined(default)
- 보조기기에 정보를 전달하지 않는다는 것을 의미한다.
- 접근성 API(보조기기 접근 가능성) 차단 상태를 결정.
- 예를 들면 모달 대화상자를 화면에 표시할 때 모달 대화상자 뒤 본문 콘텐츠에 aria-hidden="true" 속성을 선언하면 보조기기가 무시.

```html
<!-- O: 모달 윈도우를 표시할 때 다른 요소를 차단 -->
<body>
    <div class="container" aria-hidden="true">
        // 보조기기가 무시하는 영역
    </div>
    <div role="alertdialog" aria-modal="true" aria-labelledby="TITLE" aria-describedby="DESCRIPTION">
        <h2 id="TITLE">레진패스 안내</h2>
        <p id="DESCRIPTION">이 작품의 유료 에피소드 열람 시 자동으로 구매합니다. 레진패스를 적용하시겠습니까?</p>
        <button type="button">레진패스 적용</button>
        <button type="button">취소</button>
    </div>
</body>
```

#### aria-invalid

- true | false(default) | grammar | spelling
- 주로 `<input>` 요소에 선언. 사용자가 입력한 값이 요구하는 형식과 일치하는지 여부를 나타낸다.
- aria-errormessage 속성과 함께 사용하여 오류 설명을 제공할 수 있다.
- aria-invalid 는 주로 true 또는 false 값을 사용하는데 false는 오류가 없다는 것을 의미한다.
- aria-invalid 속성을 선언하지 않거나 값이 없으면 false로 간주.

```html
<!-- O: 입력 값이 유효하면 aria-invalid 속성을 생략 -->
<!-- O: 입력 값이 오류이면 aria-invalid="true" 속성을 선언 -->

<label for="email">이메일</label>
<input id="email" type="email" required value="..." aria-invalid="true" aria-errormessage="email-error-msg">
<p id="email-error-msg" aria-role="alert" aria-live="assertive">이메일 형식이 유효하지 않습니다. 앳(@)과 마침표(.)를 포함해 주세요.</p>
```

#### 실전 ARIA – 속성 (properties)

##### 실무에서 주로 사용했던 ARIA 속성들

```html
<element aria-controls="ID reference list"> ⭐
<element aria-live="polite|assertive|off(default)"> ⭐
<element aria-labelledby="ID reference list"> ⭐
<element aria-label="string">
<element aria-describedby="ID reference list">
<element aria-errormessage="ID reference"> ⭐
<element aria-modal="true|false(default)"> ⭐
```

##### aria-controls

- 현재 요소가 제어하는 대상을 명시.
- 주로 role="tab", aria-haspopup, aria-expanded 속성과 함께<button>, <a> 요소가 무엇을 제어하는지 명시.
- 값은 하나 이상의 ID 참조. 값이 여럿인 경우 공백으로 분리.

```html
<!-- O: role="tab" 요소에 aria-controls 속성 사용 -->
<button type="button" id="mon-anchor" aria-controls="mon" role="tab" aria-selected="true">월</button>

<!-- O: aria-haspopup 속성과 함께 aria-controls 속성 사용 -->
<button type="button" aria-haspopup="dialog" aria-controls="login-dialog">로그인</button>

<!-- O: aria-expanded 속성과 함께 aria-controls 속성 사용 -->
<button type="button" aria-controls="answer-99" aria-expanded="false">보너스 코인은 언제 소진되나요?</button>
```

- role="tab"에 aria-controls="mon"을 적용한 의미 : mon이라는 내용을 제어하려고 한다.
- aria-haspopup="dialog" 인 요소에 aria-controls="login-dialog" 의미 : 지금 이 버튼이 제어하려는 대상은 login-dialog 이다. 라는 의미이다.
- aria-expanded="false 또는 true" 버튼에 aria-controls="answer-99" 의미 : 이 버튼이 제어하려는 대상이 무엇인지 구체적으로 알 수 있게 된다.

