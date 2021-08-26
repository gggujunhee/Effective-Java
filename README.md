# 📙 Effective Java Study

## Item 1 : 생성자 대신 정적 팩터리 메서드를 고려하라

### 장점
- 이름을 가질 수 있다.
- 호출될 때마다 인스턴스를 새로 생성하지는 않아도 된다.
- 반환 타입의 하위 타입 객체를 반환할 수 있는 능력이 있다.
- 입력 매개변수에 따라 매번 다른 클래스의 객체를 반환할 수 있다.
- 정적 팩터리 메서드를 작성하는 시점에는 반환할 객체의 클래스가 존재하지 않아도 된다.

### 단점
- 상속을 하려면 public이나 protected 생성자가 필요하니 정적 패터리 메서드만 제공하면 하위 클래스를 만들 수 없다.
- 정적 팩터리 메서드는 프로그래머가 찾기 어렵다.

### 명명 컨벤션
- **from** : 매개변수를 하나 받아서 해당 타입의 인스턴스를 반환하는 형변환 메서드
  - **example)** ``` Date d = Date.from(instant); ```
- **of** : 여러 매개변수를 받아 적합한 타입의 인스턴스 반환하는 집계 메서드 
  - **example)** ``` Set<Rank> faceCards = EnumSet.of(JACK, QUEEN, KING); ```
- **valueOf** : from과 of의 더 자세한 버전
  - **example)** ```go BigInteger prime = BigInteger.valueOf(Integer.MAX_VALUE); ```
- **instance 혹은 getInstance** : (매개변수를 받는다면) 매개변수로 명시한 인스턴스를 반환하지만, 같은 인스턴스임을 보장하지 않는다.
  - **example)** ``` StackWalker luke = StackWalker.getInstance(options); ```
- **create 혹은 newInstance** : instance 혹은 getInstance와 같지만, 매번 새로운 인스턴스를 생성해 반환함을 보장한다.
  - **example)** ``` Object newArray = Array.newInstance(classObject, arrayLen); ```
- **getType** : getInstance와 같으나, 생성할 클래스가 아닌 다른 클래스에 팩터리 메서드를 정의 할 때 쓴다. "**_Type_**"은 팩터리 메서드가 반환할 객체의 타입이다.
  - **example)** ``` Object newArray = Array.newInstance(classObject, arrayLen); ```
- **newType** : newInstance와 같으나, 생성할 클래스가 아닌 다른 클래스에 팩터리 메서드를 정의 할 때 쓴다. "**_Type_**"은 팩터리 메서드가 반환할 객체의 타입이다.
  - **example)** ``` BufferedReader br = Files.newBufferedReader(path); ```
- **Type** : getType과 newType의 간결한 버전
  - **example)** ``` Collections.list(legacyLitany); ```
  
 
