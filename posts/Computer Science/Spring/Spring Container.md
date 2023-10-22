---
tags: Spring
---
# Spring Container(스프링 컨테이너)란?
- 스프링 프레임워크의 핵심 부분 중 하나로, 애플리케이션의 컴포넌트(빈, Bean)들을 생성, 관리 및 제어하기 위한 컨테이너이다. 
- 스프링은 자바 기반의 애플리케이션을 개발할 때 사용되며, 스프링 컨테이너는 이러한 애플리케이션의 객체 생명주기와 의존성을 관리하는 역할을 한다.

## 스프링 컨테이너의 두 가지 주요 유형
### 1. BeanFactory
- BeanFactory는 스프링 컨테이너의 최상위 인터페이스이며, 가장 기본적인 기능을 제공
- BeanFactory는 빈(Bean)의 생성, 초기화, 의존성 주입, 소멸 등을 관리

### 2. ApplicationContext
- ApplicationContext는 BeanFactory를 확장한 인터페이스
- 빈의 미리 로딩, AOP(Aspect-Oriented Programming) 지원, 국제화 및 메시지 처리, 이벤트 발행 및 처리 등 다양한 기능을 제공
- 또한, 웹 애플리케이션에서 사용되는 WebApplicationContext와 같이 특화된 ApplicationContext 구현체도 존재

## 스프링 컨테이너의 장점
- 스프링 컨테이너를 사용하면 개발자는 객체의 생성 및 의존성 관리를 스프링 프레임워크에 위임할 수 있다.
- 이를 통해 애플리케이션의 유연성, 유지보수성, 테스트 용이성 등을 향상시킬 수 있다.
- 스프링 컨테이너는 런타임 환경에서 빈들을 관리하므로, 객체의 생명주기와 스코프에 대한 관리도 제공한다.

---

# 스프링 컨테이너 생성

```
AnnotationConfigApplicationContext ac = new 
AnnotationConfigApplicationContext(AppConfig.class);
```

- **ApplicationContext** : 스프링 컨테이너(인터페이스)
- 스프링 컨테이너는 XML, 애노테이션 기반의 자바 설정 클래스로 만들 수 있음
- AnnotationConfigApplicationContext(AppConfig.class) 
  -> ApplicationContext 인터페이스의 구현체
- 애노테이션 기반 자바 설정 클래스 AppConfig


```
package hello.core;

import hello.core.discount.DiscountPolicy;
import hello.core.discount.FixDiscountPolicy;
import hello.core.discount.RateDiscountPolicy;
import hello.core.member.MemberRepository;
import hello.core.member.MemberService;
import hello.core.member.MemberServiceImpl;
import hello.core.member.MemoryMemberRepository;
import hello.core.order.OrderService;
import hello.core.order.OrderServiceImpl;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {

    @Bean
    public MemberRepository memberRepository(){
        return new MemoryMemberRepository();
    }

    @Bean
    public DiscountPolicy discountPolicy(){
        return new RateDiscountPolicy();
    }

    @Bean
    public MemberService memberService() {
        return new MemberServiceImpl(memberRepository());
    }

    @Bean
    public OrderService orderService() {
        return new OrderServiceImpl(new MemoryMemberRepository(), discountPolicy());
    }
}
```

## 스프링 컨테이너 생성 과정
### 1. 스프링 컨테이너 생성
![](https://i.imgur.com/GfSIdrP.png)
- 스프링 컨테이너를 생성할때는 구성 정보를 지정해야함

### 2. 스프링 빈 등록
![](https://i.imgur.com/WDtE1Od.png)
- 스프링 컨테이너는 파라미터로 넘어온 설정 클래스 정보를 사용해서 스프링 빈을 등록
- 빈이름 직접 부여 가능 *(주의! 빈 이름은 항상 다른 이름 부여)*

### 3. 스프링 빈 의존관계 설정 - 준비
![](https://i.imgur.com/cSjVH4N.png)

### 4. 스프링 빈 의존관계 설정 - 완료
![](https://i.imgur.com/boy9zrr.png)
