# PSA 

AS-IS

- 확장성이 좋지 못한 코드 OR 기술에 특화되어 있는 코드 

TO-BO

- 잘 만든 인터페이스(PSA)

### 스프링에서 제공하는 PSA

- 스프링에서 제공하는 대부분에 API가 전부 PSA라고 보면 된다.
- https://docs.spring.io/spring/docs/current/spring-framework-reference/



### Transaction

- PlatformTransactionManager
  - JpaTransactionManager
  - DatasourceTransactionManager
  - HibernateTransactionManger
- transactional Aspect 코드는 변하지 않는다

### 캐시

- @Cacheable, @CacheEvict

- CacheManager 
  - JCacheManager
  - ConcurrentMapCacheManager
  - EhCacheCacheManager

### 스프링 웹 MVC

- Controller, RequestMapping

- Servlet | Reactive

- 톰캣, 제티, 네티, 언더토우

  