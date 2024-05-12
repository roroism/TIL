# TODAY I LEARNED

## Learned

### html 문서 로드와 이벤트

#### 주요 이벤트

HTML 문서의 생명주기에는 3가지의 주요 이벤트가 있습니다.

- DOMContentLoade
- load
- beforeunload / unload

#### 각각의 이벤트 활용

- DOMContentLoaded : DOM이 준비된 것을 확인한 후 원하는 DOM 노드를 찾아 핸들러를 등록해 인터페이스를 초기화할 때
- load : 이미지 사이즈를 확인할 때 등. 외부 자원이 로드된 후이기 때문에 스타일이 적용된 상태이므로 화면에 뿌려지는 요소의 실제 크기를 확인할 수 있음
- beforeunload : 사용자가 사이트를 떠나려 할 때, 변경되지 않은 사항들을 저장했는지 확인시켜줄 때
- unload : 사용자가 진짜 떠나기 전에 사용자 분석 정보를 담은 통계자료를 전송하고자 할 때

#### DOMContentLoaded

- DOMContentLoaded 핸들러는 문서가 로드되었을 때 실행됩니다.
- 따라서 핸들러 아래쪽에 위치한 `<img>`뿐만 아니라 모든 요소에 접근할 수 있지만,
- 이미지가 로드되는 것은 기다리지 않습니다.
- DOMContentLoaded 이벤트는 document 객체에서 발생합니다.
- 그래서 DOMContentLoaded 는 반드시 document 에 붙여져야 합니다.
- 즉, 'DOM 트리가 완성되면 DOMContentLoaded 이벤트가 발생한다' 고 생각하면 됩니다.

#### window.onload

- 이 load 이벤트는 스타일(외부 css 포함), 이미지 등의 리소스들이 모두 로드되었을 때(전체 페이지가 로드되었을 때) 실행됩니다.
    - window.addEventListener('load',function() {})
- load 이벤트는 onload 프로퍼티를 통해서도 사용할 수 있습니다.
    - window.onload = function() {}
- load 이벤트는 window 객체에 있으므로 반드시 window 객체에 사용해야 합니다.

#### window.onunload

- window 객체의 unload 이벤트는 사용자가 페이지를 떠날 때 또는 문서를 완전히 닫을 때 실행됩니다.
- unload 이벤트에선 팝업창을 닫는 것과 같은 딜레이가 없는 작업을 수행할 수 있습니다.
- 하지만 분석 정보를 보내는 것은 예외적으로 수행할 수 있습니다. (.sendBeacon())

#### window.onbeforeunload

- 사용자가 현재 페이지를 떠나 다른 페이지로 이동하려 할 때나 창을 닫으려고 할 때 beforeunload 핸들러에서 추가 확인을 요청할 수 있습니다.
- beforeunload 이벤트를 취소하려 하면 브라우저는 사용자에게 확인을 요청합니다.

