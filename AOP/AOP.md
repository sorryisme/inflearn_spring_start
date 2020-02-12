# AOP

- 흩어진 코드를 한 곳으로 모아라

### 조작하는 방법

1. 바이트 코드(.class)를 조작하는 방법

2. 프록시 패턴을 사용하기 ( 스프링에서 사용하는 기법)

   -  A라는 클래스가 있을 때 

     ```java
     class AProxy extends A {}
     ```

### AOP 적용예제

- LogExcutionTime으로 메소드 처리 시간 로딩하기

  - LogExecutionTime 애노테이션(어디에 적용할지 표시)

  ```java
  @Target(ElementType.METHOD)
  @Retention(RetentionPolicy.RUNTIME)
  public @interface LogExecutionTime {}
  ```

  - 실제 Asect(@LogExecutionTime 애노테이션 달린 곳에 적용)

  ```java
  @Component
  @Aspect
  public class LogAspect{
  	Logger logger = LoggerFactory.getLogger(LogAspect.class);
  	
  	@Around("@annotation(LogExecutionTime)")
  	public Object logExectionTime(ProceedingJoinPoint joinPoint) throws Throwable {
  		StopWatch stopWatch = new StopWatch();
          stopWatch.start();
          
          Object proceed = joinPoint.proceed();
          
          stopWatch.stop();
          logger.info(stopWatch.prettyPrint());
          
          return proceed;
  	}
  
  }
  ```

  - Annotation 대신에 표현식 또는 Bean을 설정해 줄 수도 있다.



