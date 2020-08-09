# Day 3 / 8월 6일

8강 - 스프링 AOP
- [스프링 트라이앵글](https://dailyworker.github.io/spring-triangle/) : 제어 역전(IoC, Inversion of Control), 관점 지향 프로그래밍(Aspect Oriented Programming), 서비스 추상화(Portable Service Abstraction) - 출처 : https://dailyworker.github.io/spring-triangle/ [개발못하는 개발자]
- 같은 행동을 다른 클래스, 다른 메소드에서 실행하는 것
  - ```java
    ex)
    class A {
      method a() {
        AAA
        안녕 나는 a야
        BBB
      }
      method b() {
        AAA
        안녕 나는 b야
        BBB
      }
    }

    class B {
      method c() {
        AAA
        안녕 나는 c야
        BBB
      }
    }

    // 만약에 메소드 a(), b(), c()에 같은 AAA, BBB가 동작할 때 
    // 만약 같은 동작에 수정이 있을 경우 모두 찾아서 바꿔줘야 하기 때문에 번거로움 발생, 효율성이 떨어짐 
    ```
  - ```java
    ex)
     class A {
      method a() {
        안녕 나는 a야
      }
      method b() {
        안녕 나는 b야
      }
    }

    class B {
      method c() {
        안녕 나는 c야
      }
    }

    class AAABBBB {
      method aaabbb(JoinPoint point) {
        AAA
        point.execute()
        BBB
      }
    }
    // 공통적으로 하는 것을 별도의 클래스와 별도의 메소드로 빼낸 것이 AOP이다.
    ```
  
- 다양한 AOP 구현 방법
  - 컴파일 : A.java --- (AOP) --- A.class (AspectJ)
  - 바이트코드 조작 A.java -> A.class --- (AOP) -> 메모리 (AspectJ)
  - 프록시 패턴 (스프링 AOP) : 디자인 패턴 중에 하나를 사용하여 AOP와 같은 효과를 내는 방법
  

9강 - 스프링 프록시 패턴
- [STS Junit 사용법](https://lee-mandu.tistory.com/398?category=633568) - 출처 : https://lee-mandu.tistory.com/398?category=633568 [개발/일상_Mr.lee]
- @Transaction

10강 - 스프링 @AOP 실습
- [AOP 설명](https://sjh836.tistory.com/157) - 출처: https://sjh836.tistory.com/157 [빨간색코딩]
- AOP는 설정할 수 있는 방법이 많기 때문에 공부할 것이 많다. annotation 방식의 AOP는 명시적으로 보이기 때문에 사용한다고 한다.
- [Filter, Interceptor, AOP 에 대해서](https://goddaehee.tistory.com/154) - 출처 : https://goddaehee.tistory.com/154 [갓대희의 작은 공간]

11강 - 스프링 PSA (Portable Service Abstraction)
- jsp/servlet MVC 을 통해서 웹사이트를 만들 때 servlet을 통해서 doGet()과 doPost()를 사용하여 매핑을 하게 된다.
- 하지만 Spring에서는 이렇게 구현하지 않고 GetMapping, @RequestMapping annotation을 통해서 매핑을 한다.
- springMVC와 관련된 Service Abstraction
  - @Controller 
  - @GetMapping
  - @PostMapping
- @Transactional 
  - lowLevel로 commit이나 rollback을 사용하는 것이 아니라 Transactional annotation을 통해서 구현할 수 있다.
