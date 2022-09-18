# TODAY I LEARNED

## Learned

### react-router

**react-router-dom v5 vs v6**

1. Link에서 to는 상대경로로 적으시면 됩니다
ex. '/tv' -> 'tv'

2. exact가 사라졌습니다
대신 알아서 최적의 경로를 react-router-dom이 판단하여 매칭해줍니다.

3. useRouteMatch가 useMatch로 변경되었습니다
이 또한 상대경로로 작성하는 것으로 변경되었습니다
ex. useRouteMatch('/tv') -> useMatch('tv')

https://reactrouter.com/docs/en/v6/upgrading/v5#upgrade-to-react-router-v6
