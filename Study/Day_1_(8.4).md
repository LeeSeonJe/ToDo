# Day 1 / 8월 4일

##### 인프런 - 예제로 배우는 스프링 입문
##### inflearn Spring sample project PetClinic

### Spring start
- 배우는 이유 : spring boot에서 실제 소스의 동작이 어떻게 되는지 익히기 위해서

##### 1강
- 우선 강의는 intellij IDE를 사용하지만 STS를 사용할 예정
- [스프링 예제 소스 펫클리닉 Git site](https://github.com/spring-projects/spring-petclinic)
- 예제 소스를 STS를 사용하여 clone 할 예정
- maven package build를 실행하면 프로젝트를 package 파일을 만들어 주는데 pom.xml > project에 packaging 설정을 안하면 자동으로 jar 프로젝트가 된다.  [참고 사이트](https://jeong-pro.tistory.com/168)
- javaApplication 으로 실행할 경우 ./mvnw package 실행해야함. package 과정중에 프론트엔드 관련된 것들이 plugin 되기 때문

##### 2강
- Spring boot는 톰켓이 내장되어 있다.
- log를 보기 위해서 src/main/resources/application.properties 에 logging.level.org.springframework.veb=DEBUG 
- DEBUG를 보면서 클릭했을때 controller의 어느 메소드가 실행되는지 확인
- STS 디버깅 모드 사용시 메소드 line 앞부분 더블 클릭을 하면 break point가 걸림 / 동작하였을 때 걸리면 매핑되는 값을 볼 수 있음 / F8을 통해 다음으로 넘어감

##### 3강
- 과제풀이
  - lastName 검색을 firstName으로 검색하기 : getter와 setter을 통해서 lastName을 firstName으로 변경 / Repository, ControllerTest 부분 메소드명 변경
  - 정확한 일치가 아닌 해당 키워드로 검색하기 : Repository 쿼리문 수정 / jpa이므로 나중에 더 배울 것 / :변수명? 이런식으로 사용하는 것 같음 / %:변수명% 으로 변경
  - Owner Age 추가 : Owner에 필드 추가 / int형이 아니라 Integer형으로 선언 : 뷰로 넘어올 때 int의 기본값인 0을 가져와서 value값으로 0이 들어감 Integer은 null을 받을 수 있어서 사용



### ERROR
- error 1) No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK?
  - [해결방법](https://mainia.tistory.com/5629) - 이클립스는 자동적으로 JRE를 연결 > Preferences에서 JRE를 JDK로 바꾼다.
- error 2) Web server failed to start. Port 8080 was already in use.
  - [해결방법](https://dundung.tistory.com/148) - 잘못 빌드하여 8080 포트를 pid를 통해서 내림 / 만약 터미널에서 java -jar target/*.jar를 사용하여 실행하였으면 ctrl + c로 내릴 수 있음
