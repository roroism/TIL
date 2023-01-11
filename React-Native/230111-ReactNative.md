# TODAY I LEARNED

## Learned

### React Native

#### Layout System

React Native에서 레이아웃을 만들려면 Flexbox를 사용해야 합니다.
React Native의 Flexbox는 웹에서와 거의 같은 방식입니다.(공식문서)
https://reactnative.dev/docs/flexbox

React Native 에서는 display: block, display: inline-block, display: grid가 없습니다.
Flexbox만 사용하면됩니다.

하지만 웹에서와 다른점은 flex Direction 의 기본값은 Column입니다. 그래서 row로 직접 지정해주어야 가로로 배치됩니다.
웹에서는 flex Direction의 기본값이 row이었습니다.

flex 속성을 이용하여 비율로만 표현합니다.

가로 또는 세로로 화면을 넘어서 overflow된다고 웹처럼 scrollbar가 생기지 않습니다.
