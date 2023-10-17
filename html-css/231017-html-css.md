# TODAY I LEARNED

## Learned

### 웹 접근성 오류 유형 12개 리뷰

#### role="tablist | tab | tabpanel"

- 탭 스타일(모양)을 의미하는 것이 아님. 현재 페이지 내용에 색인을 제공하는 구조(tablist, tab, tabpanel)를 의미.
- tabpanel은 탭의 내용을 의미.
- 사이트 탐색 도구에 해당하는 요소는 nav > h2 + ul 또는 aside > h2 + ul 구조로 마크업.

```html
<div class="weekly">
  <div role="tablist">
    <button id="mon-anchor" aria-controls="mon" role="tab" aria-selected="true">월</button>
    <button id="tue-anchor" aria-controls="tue" role="tab" aria-selected="false">화</button>
  </div>
  <div id="mon" tabindex="0" role="tabpanel" aria-labelledby="mon-anchor">
    월요일엔 빨간 장미를...
  </div>
  <div id="tue" tabindex="0" role="tabpanel" aria-labelledby="tue-anchor" hidden>
    화요일엔 노란 장미를...
  </div>
</div>
```

- tablist는 탭 하나하나를 그룹핑하는 역할이다.
- tab은 탭 하나를 탭이라고 부른다.
- tabpanel은 탭 아래쪽에 표시하고있는 컨텐츠 영역을 의미한다.

#### role="tooltip"

- 보통 초점을 받으면 설명을 표시하는 문맥 팝업. (키보드의 초점을 받거나, 마우스를 올렸을 때 나오는 문맥 팝업)
- 툴팁은 초점을 받지 않아야 한다. ESC 또는 마우스를 빼면 사라져야 한다. 예를 들어 마우스를 올리거나 키보드 초점이 툴팁안으로 이동하면 안되고, 툴팁안에 링크나 버튼이 있거나 하면 안된다.
- 툴팁은 그 안에 초점을 받는 요소가 존재하지 않아야 한다.
- 참조하는 콘트롤(anchor나 button을 의미)에는 aria-describedby="ID reference list" 속성으로 연결할 수 있다.
- ID reference list 라는 것은 여러개의 ID 값 목록을 여기에 전부 연결할 수 있다는 의미이다. (2개이상이면 공백으로 분리하여 입력한다.)
- 초점이 링크나 버튼에 들어가면 툴팁을 자동으로 화면낭독기 또는 보조기기에 전달하게 된다.

```html
<!-- O: 인풋 툴팁 -->
<label for="tel">전화번호</label>
<input id="tel" type="tel" aria-describedby="TIP-TEL">
<p id="TIP-TEL" role="tooltip" hidden>하이픈(-) 없이 숫자만 입력.</p>

<!-- O: 버튼 툴팁 -->
<button aria-describedby="TIP-DEL">게시물 삭제</button>
<p id="TIP-DEL" role="tooltip" hidden>게시물 삭제 후 복원할 수 없음.</p>
```

#### role="status"

- 실시간 결과 정보. role="alert" 만큼 중요하지는 않음.
- 평범한 안내 단순 실행결과 통보 등을 알려줄 때, 사용하면 적절하다.
- role="alert"와 같이 기억하면 좋다.
- 이 요소를 갱신할 때 초점을 받지 않아야 한다.
- 이 역할을 선언하면 자동으로 aria-live="polite", aria-atomic="true" 속성이 할당됨. 이것이 의미하는 바는 aria-live="polite" 으로 설정하게 되면 보조기기는 이미 진행중인 음성을 끈지 않고, 기다렸다가 나중에 전달한다. aria-atomic="true"는 내용이 갱신이 되었을 때 부분적으로 갱신이 되었더라도 그 문장 전체( aria-atomic="true" 영역 전체)를 다시 읽어 준다.

```html
<!-- O: 결과 메시지 -->
<p role="status">회원가입 양식 전송완료.</p>
<p role="status">10개의 검색 결과.</p>
<p role="status">장바구니에 5개의 항목.</p>
<output>회원가입 양식 전송완료.</output>
<output>10개의 검색 결과.</output>
<output>장바구니에 5개의 항목.</output>
```

- 의미론에 따라 role="status" 대신 <output> 요소 사용 가능.

