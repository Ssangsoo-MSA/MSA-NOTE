# MSA-NOTE
Spring Cloud로 개발하는 마이크로서비스 애플리케이션(MSA) 을 수강하면서 필요한 note 정리


### **AntiFragile**의 특징 

- Auto scaling
	- 자동 확장성 -> 사용량에 따라 자동으로 서버 인스턴스를 증가.
- Microservices
	- 클라우드 네이티브 아키텍처, 클라우드 네이티브 애플리케이션의 핵심
- Chaos engineering
	- 시스템이 급격하고 예측하지 못한 상황이라도 견딜 수 있고 신뢰성을 쌓기 위해 운영 중인 소프트웨어 시스템에 실험하는 방법 혹은 규칙
- Continuous deployments(지속적인 배포)
	- CI/CD 필수 -> 하지 않으면 빌드 배포 자체로 일이 됨.


#### Cloud Native Architecture
- 확장 가능한 아키텍처
	- 시스템의 수평적 확정에 유연
	- 확장된 서버로 시스템의 부하 분산, 가용성 보장
	- 시스템 또는, 서비스 애플리케이션 단위의 피키지(컨테이너 기반 패키지)
	- 모니터링
- 탄력적 아키텍처
	- 서비스 생성-통합-배포, 비즈니스 환경 변화에 대응 시간 단축
	- 분활 된 서비스 구조
	- 무상태 통신 프로토콜
	- 서비스의 추가와 삭제 자동으로 감지
	- 변경된 서비스 요청에 따라 사용자 요청 처리(동적 처리)
- 장애 격리(Fault isolation)
	- 특정 서비스에 오류가 발생해도 다른 서비스에 영향을 주지 않음

#### Cloud Naitve Application
- 클라우드 네이티브 아키텍처에 의해 설계되고 구현되는 애플리케이션
- 마이크로 서비스로 개발됨
- CI/CD로 배포됨
	- 기획 - 구현 - 테스트 - 빌드 - 배포
- 컨테이너 가상화 기술을 사용함.


**※ Countinous Integration(지속적인 통합)**
- 하나의 애플리케이션을 여러 팀이나 여러 개발자에 의해서 함께 개발하고 잇는 경우 결과물을 통합하기 위한 형상관리 혹은 통합된 코드를 빌드하고 테스트하는 과정 자체를 의미하는 뜻으로 사용

**※ CD(지속적인 배포)**
- **Continuous Delivery**
	- 지속적인 전달
	- 패키지화되어 있는 결과물을 실행 환경에 수작업으로 배포하는 과정
- **Continuous Deployment**
	- 지속적인 배포
	- 운영자 혹은 관리자의 개입 없이 실행 환경까지 완벽하게 자동화되어 배포되는 과정


#### 카나리 배포와 블루그린 배포
- 카나리 배포
	- 95% 정도의 사용자는 이전 버전의 서비스를 계속 사용하도록 하고, 5% 의 사용자만이 새로운 버전의 서비스를 사용하게 하면서 서비스를 새버전으로 점진적으로 이전시키는 방법  
- 블루그린 배포
	- 사용자 트래픽을 이전 버전에서 새 버전으로 완전히 이전시키는 방법 

---


#### 스프링 클라우드란?

- 모놀리스와 달리 **서비스를 독립적으로 개발하는 마이크로 서비스 아키텍처(MSA)를 지원하기 위한 프레임워크**이다.
- 스프링 클라우드를 사용하기 위해서는 스프링 부트를 사용해야 한다.
	- 스프링 클라우드와 스프링 부트의 버전을 맞추지 않으면 특정 라이브러리가 사용되지 못하거나 사용하는 방법이 바뀌는 경우가 있다. 따라서 버전을 맞춰줘야한다.
	- `https://spring.io/projects/spring-cloud#overview` 해당 url에서 맞는 버전을 확인할 수 잇다.


#### 공식문서

Spring Cloud provides tools for developers to quickly build some of the common patterns in distributed systems (e.g. configuration management, service discovery, circuit breakers, intelligent routing, micro-proxy, control bus, short lived microservices and contract testing). Coordination of distributed systems leads to boiler plate patterns, and using Spring Cloud developers can quickly stand up services and applications that implement those patterns. They will work well in any distributed environment, including the developer’s own laptop, bare metal data centres, and managed platforms such as Cloud Foundry.

```
Spring Cloud는 개발자가 분산 시스템에서 일반적인 패턴(예: 구성 관리, 서비스 검색, 회로 차단기, 지능형 라우팅, 마이크로 프록시, 제어 버스, 수명이 짧은 마이크로 서비스 및 계약 테스트)을 빠르게 빌드할 수 있는 도구를 제공합니다. 분산 시스템의 조정은 보일러 플레이트 패턴으로 이어지고 Spring Cloud를 사용하는 개발자는 이러한 패턴을 구현하는 서비스와 애플리케이션을 빠르게 구축할 수 있습니다. 개발자의 랩톱, 베어 메탈 데이터 센터 및 Cloud Foundry와 같은 관리 플랫폼을 포함한 모든 분산 환경에서 잘 작동합니다.
```


#### 스프링 클라우드 사용시 사용되어야 하는 서비스들

- **Spring Cloud Config Server** 
	- 스프링 클라우드를 사용시 `Configuration` 정보는 따로 외부에 두게 되는데 이 때 사용하는 서비스다.
	- 변경사항이 생기더라도 재빌드/재배포를 하는 것이 아니라, 저장소의 데이터 값만 변경하여 재빌드/재배포 과정 없이 적용되도록 한다. -> **유지보수가 쉬워진다.**
- **Naming Server(Eureka)**
	- 서비스 등록과 위치정보 확인, 검색 등 서비스를 위해서 사용한다.
- **Spring Cloud Gateway**
	- 서버에 들어왔던 요청 정보를 분산하기 위한 용도로 로드 밸런싱 혹은 Gateway 기능으로 사용한다. 
	- 외부의 클라이언트 정보 혹은 서비스의 정보가 게이트웨이를 통과해서 마이크로 서비스로 진입점을 옮겨간다.
	- Gateway도 역시 Naming Server에 등록한다.
- **RestClient / FeignClient**
	- 각각의 마이크로 서비스끼리 Rest API 통신을 하도록 하기 위해서 RestClient 혹은 FeignClient 를 이용해서 데이터 통신을 하게 된다.
- **Zipkin Distributed Tracing / Netflix API gateway**
	- 시각화와 모니터링의 분산 추적을 하기 위해 사용한다.
- **Hystrix**
	- 장애가 발생했을 때 빠르게 복구하기 위한 회복성 패턴을 사용하기 위해 사용한다.

---

