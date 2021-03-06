## 🔎 디자인 패턴

---

- 실제 개발 환경에서 비즈니스 요구 사항을 프로그래밍으로 처리하면서 만들어진 다양한 해결책 중에서 많은 사람들이 인정한 베스트 프랙티스를 정리
- 객체 지향 특성과 설계 원칙을 기반으로 구현
- 객체 지향의 특성 중 상속(extends), 인터페이스(interface/implements), 합성(객체를 속성으로 사용)을 이용

---
**[어댑터패턴(Adapter Pattern)]**

  ***호출 당하는 쪽의 메서드를 호출하는 쪽의 코드에 대응하도록 중간에 변환기를 통해 호출하는 패턴***

- 개방 폐쇄 원칙을 적용
- 참고 예제 : [https://codedot.co.kr/7](https://codedot.co.kr/7)


**[프록시패턴(Proxy Pattern)]**

  ***제어 흐름을 조정하기 위한 목적으로 중간에 대리자를 두는 패턴***

- 대리자는 실제 서비스와 같은 이름의 메서드를 구현한다. 이때 인터페이스를 사용한다.
- 대리자는 실제 서비스에 대한 참조 변수를 갖는다(합성). 
- 대리자는 실제 서비스의 같은 이름을 가진 메서드를 호출하고 그 값을 클라이언트에게 돌려준다.
- 대리자는 실제 서비스의 메서드 호출 전후에 별도의 로직을 수행할 수도 있다.
- 개방 폐쇄 원칙, 의존 역전 원칙 적용

**[데코레이터 패턴(Decorator Pattern)]**

  메서드 호출의 반환값에 변화를 주기 위해 중간에 장식자를 두는 패턴

    - 프록시 패턴 vs 데코레이터 패턴
        - 프록시 패턴 : 호출에 대한 흐름 제어가 주목적, 클라이언트가 최종적으로 돌려 받는 반환값을 조작하지 않고 그대로 전달
        - 데코레이터 패턴 : 반환값에 대한 조작이 주목적이며 클라이언트에게 반환 결과에 장식을 더하여 전달

**[싱글턴 패턴(Singleton Pattern)]**

***클래스의 인스턴스, 즉 객체를 하나만 만들어 사용하는 패턴***

```java
    public class Singleton {
        static Singleton singletonObject; // 정적 참조 변수
    	
        private Singleton() {}; // private 생성자
    	
        // 객체 반환 정적 메서드
        public static Sigleton getInstance() {
            if (singletonObject == null) {
                singletonObject = new Singleton();
            }
    		
            return singletonObject;
        }
    }
```

- new를 실행할 수 없도록 생성자에 private 접근 제어자를 지정한다.
- 단일 객체 참조 변수를 정적 속성으로 갖는다.
- 단일 객체 참조 변수가 참조하는 단일 객체를 반환하는 getInstance() 정적 메서드를 갖는다.


**[템플릿 메서드 패턴(Template Method Pattern)]**

  ***상위 클래스의 견본 메서드에서 하위 클래스가 오버라이딩한 메서드를 호출하는 패턴***

  | 템플릿 메서드 패턴의 구성 요소 | 하위 클래스 |
  | --- | --- |
  | 템플릿 메서드<br/>공통 로직을 수행, 로직 중에 하위 클래스에서 오버라이딩한 추상 메서드/훅 메서드를 호출 |  |
  | 템플릿 메서드에서 호출하는 추상 메서드<br/>하위 클래스가 반드시 오버라이딩 | 오버라이딩 필수 |
  | 템플릿 메서드에서 호출하는 훅(Hook, 갈고리) 메서드<br/>하위 클래스가 선택적으로 오버라이딩한다. | 오버라이딩 선택 |

**[팩토리 메서드 패턴(Factory Method Pattern)]**

  ***오버라이드된 메서드가 객체를 반환하는 패턴***

**[전략 패턴(Strategy Pattern)]**

  ***클라이언트가 전략을 생성해 전략을 실행할 컨텍스트에 주입하는 패턴***

- 같은 문제의 해결책으로 상속을 이용하는 템플릿 메서드 패턴과 객체 주입을 통한 전략 패턴 중 선택/적용할 수 있다.
- 개방 폐쇄 원칙과 의존 역전 원칙 적용
  
**[템플릿 콜백 패턴(Template Callback Pattern)]**

  ***전략을 익명 내부 클래스로 구현한 전략 패턴***


    💡 익명 내부 클래스
    객체 = new 인스턴스() {
      해당 인스턴스가 가지고 있는 특정 메서드를 재정의해서 사용 가능
    }