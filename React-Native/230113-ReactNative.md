# TODAY I LEARNED

## Learned

### React Native

#### ScrollView

ScrollView는내부에 컴포넌트와 뷰들을 자식으로 담을 수 있는, 화면의 스크롤을 사용할 때 쓰는 컴포넌트입니다.
스크롤 방향은 horizontal을 통해 가로 또는 세로로 변경할 수 있습니다.
ScrollView에는 매우 많은 props들이 있습니다.

##### 속성 : horizontal

horizontal 속성을 추가하면 컴포넌트들이 가로로 정렬되며 scroll이 가로로 생성됩니다.

##### 속성 : contentContainerStyle

ScrollView에서 style을 적용하려면 속성 contentContainerStyle를 사용해야 합니다. (공식문서 참고)

##### 속성 : pagingEnabled

true인 경우 스크롤할 때 스크롤 뷰 크기의 배수에서 스크롤 뷰가 중지됩니다. 수평 페이지 매김에 사용할 수 있습니다.

흔히 경험이 있는..스크롤을 일정 한계이상 넘겨야 다음 페이지로 넘어가게 만들어 줍니다. 각각의 페이지처럼 만들어 줍니다.

##### 속성 : showsHorizontalScrollIndicator

true인 경우 가로 스크롤 표시기를 표시합니다.

#### Dimensions

스마트폰 화면 크기값을 얻을 수 있습니다.

이제 ScrollView 안에 있는 컴포넌트들에 적용되어 있는(ScrollView 안에 들어가 있어서 더이상 작동되지 않는)  Flex속성 대신에 사용하여 한 화면에 하나의 Day 값만 나오게 하고, 다음 날짜 는 가로 스크롤을 통해 표시되게 할 수 있습니다.

```javascript

import {Dimensions} from 'react-native';

const windowWidth = Dimensions.get('window').width;
const windowHeight = Dimensions.get('window').height;

//or
const { height, width } = Dimensions.get("window");
```

