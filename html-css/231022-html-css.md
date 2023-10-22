# TODAY I LEARNED

## Learned

### 웹 접근성 오류 유형 12개 리뷰

#### aria-labelledby

- ID reference list
- 간결한 설명 참조. (label태그를 대체한다고 생각해도 된다.)
- ID(s) 값을 이용하여 내용을 참조(연결). (텍스트를 값으로 직접 입력하는것이 아니라 설명하려는 내용이 별도로 있고, 그 요소를 아이디 값을 이용하여 참조해서 연결한다.)
- 보통 hx, a, button 요소를 참조하면 적절. (실무에서 이렇게 보통 사용)
- aria-label 속성과 함께 선언하는 경우, aria-labelledby 속성이 우선순위가 높음.
- w3에서 추천하는 방식은 (aria-label 보다는) aria-labelledby 이다. (왜냐하면 aria-label은 설명텍스트를 화면에 노출하는 방식이 아니기 때문이다.) (화면에도 설명하려는 대상 text가 존재하고, 그것을 화면 낭독기에도 전달할 수 있는 구조가 가장 바람직한 구조이다.)

```html
<!-- O: 헤딩 설명 참조 -->
<section aria-labelledby="LZ-PATH" hidden>
    <h2 id="LZ-PATH">레진패스란?</h2>
    <p>이 작품의 유료 에피소드 열람 시 자동으로 구매합니다.</p>
</section>

<!-- O: 링크 설명 참조 -->
<a id="LZ-PATH" href="#LZ-PATH-TEXT">레진패스란?</a>
<div id="LZ-PATH-TEXT" aria-labelledby="LZ-PATH" hidden>
    <p>이 작품의 유료 에피소드 열람 시 자동으로 구매합니다.</p>
</div>
```

- aria-labelledby을 hx에 연결한 경우 : 키보드 영역이 section 영역에 도달했을 때, 이 section이 무엇을 위한 section인지 설명을 연결시켜줄 수 있다.
- aria-labelledby을 link에 연결한 경우 : a태그의 텍스트를 참조하게 한다. aria-labelledby의 요소가 초점을 받았을 때, a태그의 텍스트를 음성으로 전달해 준다.

#### aria-label

- '간결한' 설명(string)을 직접 제공.
- 가능한 aria-labelledby 속성을 권장.
- 설명할 다른 참조(연결) 요소가 없는 경우 사용.
- 실제로 텍스트 노드로 존재하지 않는 경우에..숨은 설명을 제공할 때 aria-label 이 적절하다.

```html
<!-- O: 참조할 설명이 없는 경우 -->
<form>
  <input type="search" aria-label="웹툰 검색">
  <button>검색</button>
</form>
```

#### aria-describedby

- ID reference list
- 자세한 설명 참조.
- 가능하면 간결한 설명(aria-label , aria-labelledby) 에서 끝나는게 좋지만, 그것만으로 충분하지 않을 때 aria-describedby 라는 속성을 이용해서 보다 상세한 내용을 참조해서 연결할 수가 있습니다.
- ID(s) 값을 이용하여 '상세한' 내용을 참조(연결).
- 주로 툴팁, 링크(a), 폼 콘트롤(input, textarea, select, button), 알럿(role="alert"),알럿 대화상자(role="alertdialog") 요소에 사용하면 적절.

```html
<!-- O: 버튼 요소에 상세한 설명 제공 -->
<button aria-describedby="TIP-DEL">게시물 삭제</button>
<p id="TIP-DEL" role="tooltip" hidden>게시물 삭제 후 복원할 수 없음.</p>

<!-- O: 알럿 대화상자 요소에 상세한 설명 제공 -->
<div role="alertdialog" aria-modal="true" aria-labelledby="TITLE" aria-describedby="DESCRIPTION">
    <h2 id="TITLE">레진패스 안내</h2>
    <p id="DESCRIPTION">이 작품의 유료 에피소드 열람 시 자동으로 구매합니다. 레진패스를 적용하시겠습니까?</p>
    <button type="button">레진패스 적용</button>
    <button type="button">취소</button>
</div>
```

#### aria-errormessage

- ID reference
- 오류 메시지 참조. 주로 <input> 요소에 선언.
- aria-invalid=true 와 함께 사용하기 적절하다.
- aria-invalid="true" 속성을 활성화하면 보조기기는 aria-errormessage 속성이 참조하는 내용을 오류 메시지로 전달.
- 오류 메시지는 '오류 원인과 해결 방법'을 포함.

```html
<!-- O: aria-invalid 값이 true이면 aria-errormessage 값을 참조 -->
<label for="email">이메일</label>
<input id="email" type="email" required value="..." aria-invalid="true" aria-errormessage="email-error-msg">
<p id="email-error-msg" role="alert" aria-live="assertive">이메일 형식이 유효하지 않습니다. 앳(@)과 마침표(.)를 포함해 주세요.</p>
```

#### aria-modal

- true | false(default)
- popup이 모달인지 아닌지 설명한다.
- 요소가 모달인지 여부를 보조기기에 전달. 보통 role="alertdialog" 또는 role="dialog" 요소와 함께 사용.
- false(default): 속성 또는 값을 선언하지 않은 경우 초기값. 모달 콘텐츠 아님.
- true: 모달 콘텐츠.
- 사용할 수 없는 요소에 aria-hidden="true" 속성을 선언해서 보조기기가 무시하도록 설정. 배경의 포인팅 기능도 차단하도록 처리. (포인팅 기능 차단은 javascript의 도움을 받아야 한다. 키보드 초점이 modal dialog 안쪽에서만 순회하도록 구현해야 한다.)

```html
<!-- O: 알럿 대화상자에 aria-modal="true" 선언 -->
<div role="alertdialog" aria-modal="true" aria-labelledby="TITLE" aria-describedby="DESCRIPTION">
    <h2 id="TITLE">레진패스 안내</h2>
    <p id="DESCRIPTION">이 작품의 유료 에피소드 열람 시 자동으로 구매합니다. 레진패스를 적용하시겠습니까?</p>
    ...
</div>

<!-- O: 대화상자에 aria-modal="true" 선언 -->
<section role="dialog" aria-modal="true" aria-labelledby="TITLE">
    <h2 id="TITLE">로그인</h2>
    <form>...</form>
</section>
```

#### 정리

- ARIA는 역할(role), 상태(status), 속성(properties) 정보를 이용해서 HTML의 접근성 문제를 해결하는 방법.
- ARIA 역할 명세는 HTML의 의미를 조금 더 보완하는 역할을 가지고 있다.
- 상태, 속성은 문서에 생동감을 불어 넣어서 장애인 사용자들이 웹 문서를 생동감 있게 이해하고 사용하는데 도움을 준다.

