# TODAY I LEARNED

## Learned

### 히어로 섹션 만들기

- 히어로 섹션이란? 페이지에 접속했을 때 페이지 상단에 있는 가장 큰 메인 영역.
- 크롬 확장 프로그램 : Image downloader 다운로드. 이것을 이용하여 우리가 클론할 페이지의 이미지들을 다운로드 한다.
- 히어로 영역 width, height를 찾아서 figma에서 rectangle을 이요하여 히어로 영역을 그린다.
- 그 후, fill 속성의 image를 선택하여 다운로드 받은 이미지를 넣는다. 이미지는 화면을 줄이고 늘려도 가운데 고정된 상태로 양옆이 잘려가는 페이지 구조 이므로 constraints 에서 가로를 left and right 로 설정한다.
- 히어로 섹션에 올라가는 텍스트도 반응형에 맞춰 가운데 정렬되게 하려면, 텍스트 양 옆에 spacing rectangle을 넣고 Resizing을 fill container로 설정, 텍스트 가로를 화면 끝까지 늘리고 가운데 정렬, constraints and Resizing 가로를 Left and right로 설정.
- mobile frame에도 똑같이 적용. 이미지는 모바일 이미지로 교체.

