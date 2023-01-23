# TODAY I LEARNED

## Learned

### Persist

앱에 저장하여 사용자가 다른 앱으로 이동하거나 앱을 닫고 다시 돌아와도 내용을 유지하게 합니다.
string만 저장가능합니다. object를 저장하려면 먼저 object를 string으로 바꿔주어야합니다.
브라우저의 local storage처럼 작동합니다. 단, await를 사용해야합니다.

#### AsyncStorage

expo에는 AsyncStorage 라는 module이 있습니다.

Async Storage는 문자열 데이터만 저장할 수 있으므로 객체 데이터를 저장하려면 먼저 직렬화해야 합니다.
JSON으로 직렬화할 수 있는 데이터의 경우 데이터를 저장할 때 JSON.stringify()를 사용하고 데이터를 로드할 때 JSON.parse()를 사용할 수 있습니다.

`expo install @react-native-async-storage/async-storage`

### 참고 url

https://docs.expo.dev/versions/v44.0.0/sdk/async-storage/

https://react-native-async-storage.github.io/async-storage/docs/usage/

### 참고

expo install은 기본적으로 npm install을 실행시킵니다.
expo install을 사용하면 현재 사용중인 expo 버전과 같은 버전의 모듈을 설치해줍니다.


