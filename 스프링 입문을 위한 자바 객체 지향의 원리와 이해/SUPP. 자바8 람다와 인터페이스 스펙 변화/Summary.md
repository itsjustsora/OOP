### 람다가 도입된 이유

---
- 하나의 CPU 안에 다수의 코어를 삽입하는 멀티 코어 프로세서들이 등장하면서 병렬화 프로그래밍에 대한 필요성이 생기기 시작
- 자바 8에서는 병렬화를 위해 **컬렉션(배열, List, Set, Map)** 을 강화했고 이러한 컬렉션을 더 효율적으로 사용하기 위해 **스트림(Stream)** 을 강화했다.
- 스트림을 효율적으로 사용하기 위해 함수형 프로그래밍이, 다시 함수형 프로그래밍을 위해 람다가, 또 람다를 위해 인터페이스의 변화가 수반됐다.
- 람다를 지원하기 위한 인터페이스를 함수형 인터페이스라고 한다.

### 람다란 무엇인가?

---
*코드 블록, 변수에 저장 가능한 로직*

**기존 방식의 코드 블록**
```java
public class B001 {
	public static void main(String[] args) {
		MyTest mt = new MyTest();

		Runnable r = mt;
		r.run();
	}
}

class MyTest implements Runnable {
	public void run() {
		System.out.println("Hello Lambda");
	}
}

or

public class B002 {
	public static void main(String[] args) {
		Runnable r = new Runnable() {
			System.out.println("Hello Lambda");
		};

		r.run();
	}
}
```

**새로운 방식의 코드 블록**

```java
public class B003 {
	public static void main(String[] args) {
		Runnable r = () -> {
			System.out.println("Hello Lambda");
		};

		r.run();
	}
}
```

- Runnable 타입으로 참조 변수 r을 만들고 있으니 new Runnable()은 컴파일러가 알아낼 수 있으므로 생략한다.
- public void run() 메서드는 Runnable 인터페이스가 가진 유일한 추상 메서드이기 때문에 ()으로 생략이 가능하다.
- **_람다의 구조_**
    - (인자 목록) → { 로직 }

### 함수형 인터페이스

---
***추상 메서드를 하나만 갖고 있는 인터페이스***

```java
public class B005 {
	public static void main(String[] args) {
		MyFunctionalInterface mfi = (int a) -> { return a * a };

		int b = mfi.runSomethig(5);
		
		System.out.println(b);
	}
}

@FuctionalInterface
interface MyFunctionalInterface {
	public abstract int runSomething(int count);
}
```

- @FunctionalInterface

  선택적으로 사용 가능하며 컴파일러는 인터페이스가 함수형 인터페이스의 조건에 맞는지 검사한다. 즉, 단 하나의 추상 메서드만을 갖고 있는지 확인한다.

**최적화된 소스**

```java
public class B006 {
	public static void main(String[] args) {
		MyFunctionalInterface mfi = a -> a * a;

		int b = mfi.runSomethig(5);
		
		System.out.println(b);
	}
}
```

- 중괄호 생략할 때는 return도 같이 생략해 줘야 한다.


### 인터페이스의 디폴트 메서드와 정적 메서드

---
- 자바 8 이전의 인터페이스 멤버
    - 정적 상수
    - 추상 인스턴스 메서드
- 자바 8
    - 정적 상수
    - 추상 인스턴스 메서드
    - 구체 인스턴스 메서드 - 디폴트 메서드
    - (구체) 정적 메서드

```java
interface MyFunctionalInterface2 {
	// 정적 상수
	public static final int constant = 1;

	// 추상 인스턴스 메서드
	public abstract void abstractInstanceMethod();

	// JAVA 8 디폴트 메서드 - 구체 인스턴스 메서드
	public default void concreteInstanceMethod() {
		System.out.println("something");
	}

	// JAVA 8 정적 메서드 - 구체 정적 메서드
	public static void concreteStaticMethod() {
		System.out.println("something");
	}
}
```
디폴트 메서드와 정적 메서드의 도입으로 기존에 작성한 프로그램들도 아무런 사이드 이펙트 없이 자바 8 JVM에서 구동된다.

