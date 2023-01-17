# TODAY I LEARNED

## Learned

### React Native

#### Icons

expo를 설치했다면
`@expo/vector-icons` 패키지를 사용할 수 있습니다.
이 패키지를 이용하여 icon을 사용할 수 있습니다.

##### Expo Vector Icons

공식문서
https://docs.expo.dev/guides/icons/

아이콘 종류
https://icons.expo.fyi/

코드사용 예

```javascript
import * as React from 'react';
import { View, StyleSheet } from 'react-native';
import Ionicons from '@expo/vector-icons/Ionicons';

export default function App() {
  return (
    <View style={styles.container}>
      <Ionicons name="md-checkmark-circle" size={32} color="green" />
    </View>
  );
}

const styles = StyleSheet.create({ ... });
```

