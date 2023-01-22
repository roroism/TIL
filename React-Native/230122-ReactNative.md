# TODAY I LEARNED

## Learned

### Object.keys(x)

Array를 사용하지 않고 hash tables를 사용했을 경우, map함수를 사용해서 jsx에서 출력하기 위해서 Object.keys(x)를 사용할 수 있습니다.

Object.keys(x) 를 사용해서 object안 key들을 array로 얻어내고, 이것을 map으로 출력합니다.

```jsx
<ScrollView>
  {Object.keys(toDos).map((key) => (
    <View key={key}>
      <Text>{toDos[key].text}</Text>
    </View>
  ))}
</ScrollView>
```

