## **스프링의 3대 프로그래밍 모델**

![스크린샷 2022-02-20 오후 11.03.31.png](https://user-images.githubusercontent.com/80027033/155329536-fe510f64-7c5e-4288-a4d4-615523f6dda1.png)

### [IoC/DI - 제어의 역전/의존성 주입]

---
**스프링을 통한 의존성 주입 - @Autowired vs @Resource**

|  | @Autowired | @Resource |
| --- | --- | --- |
| 출처 | 스프링 프레임워크 | 표준 자바 |
| 소속 패키지 | org.springframework.beans.factory.annotation.Autowired | javax.annotation.Resource |
| 빈 검색 방지 | byType 먼저, 못 찾으면 byName | byName 먼저, 못 찾으면 byType |
| 특이사항 | @Qualifier(””) 협업 | name 어트리뷰트 |
| byName 강제하기 | @Autowired<br/>@Qualifier(”tire1”) | @Resource(name=”tire1”) |


**의존 관계**

DI는 외부에 있는 의존 대상을 주입하는 것을 말한다. 의존 대상을 구현하고 배치할 때 SOLID와 응집도는 높이고 결합도는 낮추라는 기본 원칙에 충실해야 한다. 그래야 프로젝트의 구현과 유지보수가 수월해진다.


### [AOP; Aspect-Oriented Programming - 관점 지향 프로그래밍]

---
**횡단 관심사(cross-cutting concern) : 다수의 모듈에 공통적으로 나타나는 부분**

- @Aspect : AOP를 사용하겠다는 의미
- @Before : 대상 메서드 실행 전에 이 메서드를 실행하겠다는 의미
- 스프링 AOP의 핵심
    - 스프링 AOP는 인터페이스 / 프록시 /  런타임 기반이다.

### [PSA; Portable Service Abstraction - 일관성 있는 서비스 추상화]

---
어댑터 패턴을 적용해 같은 일을 하는 다수의 기술을 공통의 인터페이스로 제어할 수 있게 한 것을 서비스 추상화라고 한다.