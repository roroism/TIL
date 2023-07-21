# TODAY I LEARNED

## Learned

### 테슬라 반응형 웹사이트 구조 살펴보기

### 메뉴 바 만들기

- 메뉴 바는 보통 'gnb' 라고 부른다. 'global navigation bar'
- 다른 클론 디자인 할 때는 해당 브랜드의 브랜드 가이드를 보는 것이 좋다. 하지만 테슬라는 10년전에 나온 가이드가 있긴 하지만 큰 도움이 안된다.
- 전체 width 값 1210px 이상부터 전체 메뉴가 나오기 시작하므로 1210px를 break point 로 잡는다.
- 그다음 break point는 640px 이다. figma -> frame 으로 각각 width 값 1210px, 630px frame을 만들어 준다.
- 테슬라 로고 svg를 figma로 가져온다.
- 폰트 정보를 찾아서 실제 폰트 파일을 다운로드 한다. (사용하지 않을 것 같은 이텔릭체는 제거해도 좋다.)
- gnb의 font 크기, 마진등의 정보를 참고한다.
- gnb 버튼 영역과 그 위에 올라간 메뉴 텍스트를 합쳐서 Create component로 컴포넌트화 한다.
- gnb 컴포넌트 6개를 동시에 선택하여 Auto layout 처리 한다.
- 크기를 줄일 땐 scale 툴을 써야 이미지가 안 깨진다.
- rectangle을 이용하여 햄버거 버튼의 삼색선을 만든 후, 3개의 rectangle을 하나로 만들기 위해 Union selection 처리한다.
- Union selection 처리한 삼색 선과 햄버거 버튼의 바탕이 되는 rectangle을 같이 선택하여 Create component 화 한다.
- 컴포넌트화된 햄버거 버튼의 이름을 icons / menu 로 수정한다. 그 후 바탕 rectangle의 색을 빼면 투명화된다.
- 햄버거 버튼을 한 개 복사해서 햄버거 아이콘을 클릭하고 auto layout을 클릭하면 자동으로 padding 이 10이 적용된다. 이름을 버튼에서 쓰는 icon이라는 의미로 buttons / icon 으로 명명한다. 역시 component화 한다.
- fill에 눈 모양 아이콘을 끄면 투명화 된다. buttons / icon의 바탕 rectangle은 아이콘의 터치 범위를 의미한다.
- 왼쪽 상단 Assets 에 가면 buttons 목록에 우리가 만든 버튼이 생겼다. 드래그 and 드롭으로 가져와서 사용한다.
- 테슬라 로고는 Create component 하여 이름을 logo로 바꾼다.
- 같이 다니는 컨텐츠들 끼리는 하나의 컨텐츠라는 의미로 auto layout으로 묶어 준다. 정렬이 안되었을 때는 정렬 버튼으로 맞춰준다. 사이 간격도 조절 가능
- gnb에 들어가는 모든 컨텐츠 들을 선택하여 auto layout 처리 한다. 그 후 클론하는 사이트의 양쪽 페딩 값만큼 gnb에 페딩을 넣어준다.
- 이제 반응형을 표현할 건데 logo 같은 경우는 리사이징이 되면 안되니까 Resizing이 가로 세로 모두 Fixed 되어있다.
- gnb 메뉴들도 고정이여야 하지만, fixed가 아닌 Hug로 한다. 왜냐하면 안에 있는 text가 길어질수도 있기 때문이다. Hug란 안에 있는 내용이 길어지면 그 만큼만 길어진다의 의미다.
- 그럼 늘어나야하는 부분은 결국 아무것도 없는 사이 공간들이다. 이 사이공간에 Rectangle을 하나 넣어서 이름을 spacing이라고 짓는다. 공간이 2군대 있으니 cmd + d 로 copy 하여 하나 더 넣어준다.
- 이 gnb 바의 사이 공간을 0으로 하면 gnb안의 모든 컨텐츠가 딱 붙는 모습을 볼 수 있다. gnb 바를 마우스로 잡고 늘리거나 줄일 때마다 spacing으로 이름 지어준 rectangle 이 함께 늘거나 줄어들게 하기 위해 spacing 2개를 클릭하여 Resizing을 fill container 로 명명한다. 높이값도 fill container 해줘도 상관없다.
- 이제 gnb바를 마우스로 잡고 가로를 늘리면 같이 따라서 늘어난다.
- 높이 값을 맞춰주기 위해 gnb의 위 아래에 패딩을 넣어 높이를 늘려준다.
- gnb를 create component로 component로 만들어 준다.
- Assets에서 가져온 컴포넌트는 우리가 컴포넌트화 시킨것의 복제품이다. 그래서 원본 component에 변화를 주면 복제품들도 전부 똑같이 적용된다.
- 복제품에서 지운 것은 원본에 변화를 주지 않는다. 그리고 복제품에서 delete로 지운것은 정확하게는 아예 없어진 것이 아니라 눈만 꺼서 보이지 않게 처리될 뿐이다. 변화를 준 복제품을 원상태로 복원하려면 Reset all overrides 하면 된다.
- 이제 모바일 Layout을 작업하면 된다. 만든 gnb바를 Assets에서 복제품을 가져와서 불필요한 메뉴들을 지운 후 gnb바를 Frame 크기에 맞춘다.
- 복제품의 로고 svg의 컬러를 수정할 수 있다.
- gnb의 가로 constraints and Resizing 을 Scale 로 바꿔주면 Frame의 가로를 늘이고 줄일 때 마다 gnb도 같이 늘어나고 줄어든다.

