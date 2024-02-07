# TODAY I LEARNED

## 복습

### JSON

- JavaScript Object Notation (JSON)은 Javascript 객체 문법으로 구조화된 데이터를 표현하기 위한 문자 기반의 표준 포맷입니다.
- 웹 어플리케이션에서 데이터를 전송할 때 일반적으로 사용합니다(서버에서 클라이언트로 데이터를 전송하여 표현하려거나 반대의 경우).
- 개별 JSON 객체를 .json 확장자를 가진 단순 텍스트 파일에 저장할 수 있습니다.
- MIME 타입은 application/json

#### JSON 구조

- 위에서 설명했듯이 JSON은 Javascript 객체 리터럴 문법을 따르는 문자열입니다.

예시
```json
{
  "squadName": "Super hero squad",
  "homeTown": "Metro City",
  "formed": 2016,
  "secretBase": "Super tower",
  "active": true,
  "members": [
    {
      "name": "Molecule Man",
      "age": 29,
      "secretIdentity": "Dan Jukes",
      "powers": ["Radiation resistance", "Turning tiny", "Radiation blast"]
    },
    {
      "name": "Madame Uppercut",
      "age": 39,
      "secretIdentity": "Jane Wilson",
      "powers": [
        "Million tonne punch",
        "Damage resistance",
        "Superhuman reflexes"
      ]
    },
    {
      "name": "Eternal Flame",
      "age": 1000000,
      "secretIdentity": "Unknown",
      "powers": [
        "Immortality",
        "Heat Immunity",
        "Inferno",
        "Teleportation",
        "Interdimensional travel"
      ]
    }
  ]
}
```

#### JSON에서의 배열

- 앞서 JSON 텍스트는 기본적으로 JavaScript의 오브젝트와 비슷하게 생겼다고 언급하였습니다. 그리고 그것은 대부분 맞습니다. "대부분 맞다"라고 말한 이유는 JavaScript의 배열 또한 JSON에서 유효하기 때문입니다.

