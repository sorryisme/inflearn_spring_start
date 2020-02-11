# IOC 

Inversion of Control 



### 일반적인 의존성에 대한 제어권

- AS-IS : 기존의 객체 생성 방식

```java
private OwnerRepository repository = new OwnerRepository();
```



- 내가 쓸 객체의 자식타입이면 대체하기(유지보수하기 편함)
- 코드 테스트하기도 편함
- To-BE

```java
class OnwerController{
	private OwnerRepository repo;
	
	public OnwerController(OwnerRepository repo){
		this.repo = repo;
	}
	
}

class OwnerControllerTest{
	@Test
	public void create(){
		OwnerRepository repo = new OwnerRepository();
		OwnerController controller = new OwnerController(repo);
	}

}
```

- To-Be , 실제 코드 (생성자를 통한 의존성 주입)

```java
@Controller
class OwnerController {
	...

	private final OwnerRepository owners;
	private VisitRepository visits;
	// 생성자를 통한 의존성 주입
	public OwnerController(OwnerRepository clinicService, VisitRepository visits) {
		this.owners = clinicService;
		this.visits = visits;
	}
```

- **IOC 핵심: 나 자신이 아닌 외부에서 주입 받는다.**



### IOC 컨테이너(ApplicationContext [BeanFactory])

- Bean을 만들어주고 엮어주며 제공한다 
- 빈 설정 (오로지 빈만 관리)
  - 이름 또는 ID
  - 타입
  - 스코프

* IOC 컨테이너 또한 Bean으로 등록되어있음
  * ApplicationContext에서 Bean들을 꺼내올 수 있음



### Bean (오로지 Bean만 의존성 관리한다.)

- 스프링 IoC 컨테이너가 관리하는 객체
- Component Scanning
  - @Component
    - @Repository
    - @Service
    - @Controller
  - 직접 XML이나 자바 설정 파일에 등록 ( @Bean으로 등록하려면 @Configuation 클래스 안에서 작성)
- 꺼내쓰고 싶다면 @Autowired, @Inject, ApplicationContext.getBean으로 꺼내야함