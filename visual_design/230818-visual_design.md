# TODAY I LEARNED

## Learned

### HTML을 어떻게 공부해야 하는가

- HTML : 골격과 의미를 전달하는 언어
- https://html.spec.whatwg.org/ 에서 HTML 표준을 만들고 유지보수를 함.(브라우저 제조사 연합)
- 브라우저 구현 현황 : https://caniuse.com/
- 기존의 block 요소들은 이제는 주로 Flow 콘텐츠라고 부른다.
- HTML 명세 사이트 : https://html.spec.whatwg.org/multipage/indices.html#element-content-categories

#### Flow content (플로우 콘텐츠)

- body 에 포함할 수 있는 모든 요소.
- 예전에 block 라고 부르던 요소들도 포함이 되지만, inline 이라고 부르던 요소들도 다 포함이 된다. 즉, 대부분의 요소들은 전부 Flow contents 이다.

#### Metadata content (메타데이터 콘텐츠)

- 주로 문서의 head안에 들어가는 요소들.
- 콘텐츠와 문서를 구조화 하는 요소를 의미. 다른 콘텐츠의 표시, 동작, 관계 등을 설정.
- 경우에 따라서 일부 요소는 플로우 콘텐츠.예) script : body안에서도 사용할 수 있다.
- 이 요소들은 실제로 화면에 출력하는 요소들은 아니기 때문에 css에서는 브라우저 display: none 방식으로 화면에 표시한다.

#### Heading content (헤딩 콘텐츠)

- h1 ~ h6, hgroup
- sectioning 콘텐츠의 헤더
- sectioning 콘텐츠가 없어도 헤딩 콘텐츠가 있으면 암시적으로 섹션(==문서의 개요)이 형성된다.
- display : block

#### Sectioning content (sectioning 콘텐츠)

- article, aside, nav, section
- 자주 빈번하게 사용된다.
- 헤딩, 헤더, 풋터의 범위.
- 각각 Sectioning 콘텐츠는 암시적인 개요를 형성하고, Sectioning 콘텐츠와 헤딩 콘텐츠를 함께 사용하면 명시적인 개요를 형성한다.
- display : block

#### Phrasing content (프레이징 콘텐츠)

- 구문 콘텐츠, 단락을 형성하는 콘텐츠.
- 예전에 inline 요소라고 부르던 콘텐츠들이 대부분 프레이징 콘텐츠이다.
- 이런 요소들이 보여서 하나의 단락을 형성하고 block을 형성하게 된다.
- display : inline, inline-block, none
- display : none인 프레이징 콘텐츠들 : link, meta, noscript, script, template

#### Embedded content (임베디드 콘텐츠)

- 외부 자원을 참조하는 콘텐츠
- 모든 임베디드 콘텐츠는 구문 콘텐츠이다.
- display : inline, inline-block

#### Interactive content(인터렉티브 콘텐츠)

- 사용자와 상호 작용할 수 있는 콘텐츠
- a, button, iframe, img, input, label, select, textarea, video
- 입력 장치(키보드, 마우스)로 조작할 수 있다.
- display : inline, inline-block

#### Palpable content (팰퍼블 콘텐츠)

- 비어 있지 않은, 볼 수 있는 콘텐츠
- 화면에서 숨겨지 있지 않고, 클릭할 수 있거나 볼 수 있거나 드래그로 영역설정 등
- hidden 속성이 없는.

#### Script-supporting element (스크립트 지원 요소)

- 렌더링하지 않지만 사용자에게 기능을 제공
- script, template

#### Transparent content models (투명 콘텐츠 모델)

- 투명 콘텐츠 모델. 부모의 콘텐츠 모델을 따른다.
- 문서노드에서 제거해도 문서가 유효하게 유지되어야 하는 요소
- a, video, audio, canvas, ins, del, map...
- 자식 요소로 무엇이든 담을 수 있지만, 부모 요소가 등장했을 때는 그 맥락을 따져봐야 한다.

#### HTML 명세의 구성

- Context : 부모 요소의 콘텐츠 모데 유추 가능
- Content model : 자식 요소의 카테고리

