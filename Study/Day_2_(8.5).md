# Day 2 / 8월 5일

4강 - 스프링 IoC (Inversion of Control)
- 제어권 역전 의존성을 관리하는 일 자체가 역전되는 것이다. 자기 자신이 제어하는게 아니고 외부에 의해서 제어가 된다.
- bean : Spring이 관리하는 객체
- Spring이 bean을 통해서 만들어진 객체를 관리하고 의존성 또한 관리한다.

```java
class OwnerController {
  private OwnerRepository repo;
  // OwnerRepository를 사용하지만 객체를 만들지 않는다.  
  // OwnerController 밖에서 만들어서 줄 수 있게끔 생성자를 통해 받아온다.
  // 즉, OwnerController 안에서 의존성을 만들어 관리하는 것이 아니라 밖에서(IoC) 만들어서 받아와 사용한다.
  // 의존성 주입(Dependency Injection) 또한 일종의 IoC로 볼 수 있다. 
  // 의존성을 관리하는 일이 자기 자신이 아니라 외부에 의해서 제어가 되기 때문에
  public OwnerController(OwnerRepository repo) {
    this.repo = repo;
  }
}
```



##### IoC 컨테이너
- 

생성자를 사용한 것을 권장 - 필수적으로 사용해야하는 레퍼런스 없이는 인스턴스를 만들지 못하도록 강제화 할 수 있다.
