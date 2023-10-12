# TODAY I LEARNED

## Learned

### 웹 접근성 오류 유형 12개 리뷰

#### 표의 구성 (Info and Relationships)

화면에 전달하는 정보, 구조, 관계는 텍스트로 변환하거나 기계가 인식할 수 있어야 한다.
(표의 구성) 표는 이해하기 쉽게 구성해야 한다.

```html
<table>
    <caption>대한민국 지역별 인구 통계</caption>
    <thead>
        <tr>
            <th scope="col">년도</th>
            <th scope="col">서울</th>
            <th scope="col">대전</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">2021</th>
            <td>...</td>
            <td>...</td>
        </tr>
        <tr>
            <th scope="row">2020</th>
            <td>...</td>
            <td>...</td>
        </tr>
    </tbody>
</table>
```

##### caption 요소

- 표의 요소 안쪽에 첫번째 요소로 caption 요소를 사용한다.
- 스크린 리더 사용자는 표에 접근했을 때, caption의 내용을 전달받게 된다.

##### th 요소

- caption 다음으로 중요한 것은 th 라는 요소이다.
- table header의 약자이다. 즉, 제목 cell을 의미한다.
- th와 함께 사용해야될 속성이 scope 속성이다. scope속성은 어떤 셀을 관측(설명)하고 있는가.를 의미한다. col 값은 열, row 값은 행을 의미한다.

#### 레이블 제공 (Labels or Instructions)

콘텐츠가 사용자 입력을 요구할 때 레이블 또는 설명을 제공해야 한다.
(레이블 제공) 사용자 입력에는 대응하는 레이블을 제공해야 한다.

```html
<input value="아이디"> ❌
<input placeholder="아이디"> ❌
```

```html
<input id="xxx"> 
<label for="xxx">아이디</label> 👏
```

```html
<input aria-label="아이디"> 👌
```

- 만약 화면에 label 텍스트를 노출하지 않고 input 컨트롤만 노출하고 싶다면, 흔치않은 경우이지만 aria-label 이라는 속성안에 직접 대체 텍스를 입력하는 방법도 있다. 입력된 값은 화면에 노출되지 않는다.

#### 자막 제공 (Captions(Prerecorded))

녹음된 음성 콘텐츠에 동기화된 자막을 제공해야 한다. 미디어가 문자를 대체하기 위한 설명이면 예외. (실시간 음성 X)
(자막 제공) 멀티미디어 콘텐츠에는 자막, 대본 또는 수화를 제공해야 한다.

```html
<video poster="myvideo.png" controls>
  <source src="*.mp4" srclang="en" type="video/mp4">
  <track src="*.vtt" kind="captions" srclang="en" label="English">
  👏
</video>
```

- 위 코드처럼 자막을 제공하기 어려운 경우 한국에서 허용하는 방식으로 대본 또는 수어 제공방법이 있다.

#### 제목 제공 (Page Titled / Headings and Labels)

##### Title

웹 페이지는 주제나 목적을 설명하는 제목(title)이 있어야 한다.(A)
제목(heading)과 레이블은 주제 또는 목적을 설명해야 한다.(AA)
(제목 제공) 페이지, 프레임, 콘텐츠 블록에는 적절한 제목을 제공해야 한다.

```html
<title>XX 홈페이지에 오신 것을 환영합니다!</title> ❌
<title>▒▒▒ 특수 문자 제발 쓰지 마요.</title> ❌

<title>다른 페이지와 중복 없는 고유한 제목</title> 👏
```

- title은 검색엔진, 화면 낭독기에서 가장 중요한 text이다.

##### Heading

- 검색엔진은 Heading이 잘 정돈된 웹페이지를 좋아한다.
- 화면 낭독기는 Heading 텍스트만 따로 모아서 음성으로 전달받고, 원하는 위치로 직접 이동할 수 있다. 페이지의 목차를 제공하는 것과 같은 효과가 있다.

##### iframe에 대한 설명 제공

- aria라는 명세를 사용해서 aria-label에 설명을 제공한다.

```html
<iframe src="*.html"></iframe> ❌

<iframe src="*.html" aria-label="공시 자료"></iframe> 👏
<iframe src="*.html" aria-label="빈 프레임"></iframe> 👏
```

