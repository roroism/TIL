# TODAY I LEARNED

## Learned

### remove() 와 removeChild()의 차이

- remve() 와 removeChild() 는 기본적으로 같은 기능을 합니다.
- 다만, 사용하는데 있어서 몇가지 사소한 차이점들이 있습니다.

- remove() 는 노드를 메모리에서 삭제하고 종료합니다. 하는데 반해, 
- 반면 removeChild()는 노드를 삭제하는 것이 아닙니다. 

- 메모리에 해당 노드는 그대로 존재하며, 부모 노드와의 부모-자식관계를 끊어 DOM 트리에서 해제하는 것입니다. 최종적으로는 관계를 끊은 해당 노드의 참조를 반환합니다.

- 반환값을 변수에 저장하지 않으면 삭제하는 노드의 참조가 더이상 없기 때문에, 자바스크립트 엔진의 GC(Garbage Collection)에 의해 잠시 후 메모리에서 삭제됩니다.
