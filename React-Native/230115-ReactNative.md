# TODAY I LREANED

## Learned

### React Native

#### Location

유저 위치 정보를 가져오는 방법을 알아보겠습니다.

##### installation

`expo install expo-location`

cmd 창에 입력하여 설치합니다.
공식문서 : https://docs.expo.dev/versions/latest/sdk/location/

requestPermissionsAsync() : 유저 권한을 요청. 무조건 해야합니다. (Deprecated)

    위 메소드 대신에 아래 메소드를 사용합니다.

    requestForegroundPermissionsAsync() : 앱이 실행되는 동안 사용자에게 위치에 대한 권한을 부여하도록 요청합니다.

    requestBackgroundPermissionsAsync() : 앱이 백그라운드에 있는 동안 사용자에게 위치에 대한 권한을 부여하도록 요청합니다.

getLastKnownPositionAsync() : 유저의 마지막 위치를 받을 수 있습니다.

getCurrentPositionAsync() : 유저의 현재 위치를 받을 수 있습니다.

watchPositionAsync() : 위치를 관찰합니다. 그래서 유저가 이동을 해도 따라가면서 위치를 알 수 있습니다.

geocodeAsync() : 주소를 받아서 위도와 경도로 변환해줍니다.

reverseGeocodeAsync(location) : 위도와 경도를 이 function에 주면 도시와 구역을 반환해줍니다.

startGeofencingAsync(taskName, regions) : 유저가 특정 지역을 벗어났을 때 알려줍니다. 그래서 유저가 그 지역에 있을 수 있도록 유도할 수 있습니다. 유저가 그 지역을 들어갔을 때나 나갔을 때 우리에게 말해줍니다.

