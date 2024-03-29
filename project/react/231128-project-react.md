# TODAY I LEARNED

## Learned

### 시스템 설계 (3) - Class diagram

- 한 시스템을 구성하는 클래스들의 구조, 속성(attribute), 메소드(method)를 시각화 한 diagram.
- 클래스의 구조 및 클래스 간의 관계에 촛점을 맞춘 structural diagram.

#### 왜 사용하나요?

- 클래스 간의 관계, 의존성을 빠르게 파악할 수 있다.
    - 새로운 요구사항이 들어왔을 때, 재사용하거나 확장할 만한 클래스가 있는지 빠르게 파악 가능.
- 소프트웨어가 완성된 후 구현 설명을 위해 사용할 수 있다.
    - 새로운 팀원이 왔을 때 빠르게 시스템 구조를 파악할 수 있다.

> e.g. 50 개의 클래스가 있을 때, 50 개 파일을 다 열어두고 비교해가며 구조를 파악하는 것은 효율적이지 않음.

#### 언제 사용하나요?

- 요구사항이 수집되고, 시스템 내의 클래스 설계 단계에서
- 클래스 간의 관계가 복잡할 때 (상속과 조합이 많을 때)
- 시스템에서 사용되는 클래스들의 구조를 시각화 해야 할 때
- 새로운 시스템을 설계하거나 기존의 시스템을 확장할 때(참고용으로)

#### 구성 요소

- 클래스
    - 속성 (Attribute)
    - 메소드 (Method)
- 관계
    - 상속 (Inheritance)
    - 조합 (Composition)

