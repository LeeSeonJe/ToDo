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

5강 - 스프링 IoC 컨테이너
- Spring IoC 컨테이너의 역할 : bean을 등록하고 bean들 사이의 의존성을 엮어주며 만들어진 bean들을 제공해주는 일을 한다.
- [Spring 싱글톤 패턴](https://medium.com/webeveloper/%EC%8B%B1%EA%B8%80%ED%84%B4-%ED%8C%A8%ED%84%B4-singleton-pattern-db75ed29c36)


6장 - 스프링 빈(bean)
- applicationContext가 관리하는 객체에서 가져오는(담고있는) 객체가 bean이다. @SpringBootApplication 안에 @ComponentScan annotation이 하위 폴더에 @Component를 찾으라고 알려줌
- 어떻게 spring 컨테이너 안에 bean을 만들어 줄까?
  - Component scanning : 밑에 있는 annotation을 찾아서 클래스의 인스턴스를 만들어서 bean으로 등록하는 일을 한다. 
    - @Component : 안에 있는 annotation
      - @Repository : 조금 다르게 bean이 생성된다. interface ~... 어쩌구 Spring + jpa에서 설명이 있음.
      - @Service
      - @Controller
      - @Configuration
  - 직접 XML이나 자바 설정파일에 등록
    - 자바 설정파일에 등록하기 
    ```java
    @Configuration
    public class SampleConfig {
      @Bean
      public SampleContorller sampleContoroller() {
        return new SampleController();
        // 이렇게 하면 @Controller 생략 가능
      }
    }
    ```
bean 객체를 꺼내 쓰는 방법
- @AutoWired annotation 사용하여 IoC 컨테이너에 들어있는 bean을 주입받아서 사용할 수 있다.

7강 - 의존성 주입 (Dependency Injection)
- 의존성 주입 방법
  - @Autowired, @Injection : final 키워드가 있으면 안된다. final은 생성과 동시에 초기화를 해줘야한다.
  - 생성자
  - Setter
- 생성자를 사용한 것을 권장 - 필수적으로 사용해야하는 레퍼런스 없이는 인스턴스를 만들지 못하도록 강제화 할 수 있다.
- 과제 
  - PetRepository 주입하기.
    - 1. @Autowired 이용하기 (필드선언)
      - ```java  
        @Autowired
        private PetRepository petRepository;
        ```
    - 2. 생성자
      - ```java
        private final PetRepository petRepository;

        public OwnerController(PetRepository petRepository) {
          this.petRepository = petRepository;
        }

        ```
    - 3. Setter
      - ``` java
        @Autowired
        public void setPetRepository (PetRepository petRepository) {
          this.petRepository = petRepository;
        }
        ```
