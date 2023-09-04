---
title: Java-Spring
excerpt: 旨在掌握Spring的核心，比如IOC容器以及AOP切面编程。最重要的：能不能让一个只知道Java基础的人，理解Spring。
---
## IOC核心技术
- IOC(Inversion fo Control):控制反转即将类的对象的创建和管理交给Spring类管理。这些被管理的类称为Bean
- DI(Dependency injection):将类里面的属性在创建类的过程中给属性赋值

### 0.IOC容器的实现
- TODO
### 1.组件注册：使用@Configuration和@Bean给容器中注册组件
- IOC容器采用读取配置类的方式。配置类如下：简单来说，将@Configuration添加到类上，@bean添加到类的方法上，就能将bean注入到Spring容器里面。
```java
import io.binghe.spring.annotation.chapter01.configuration.bean.Person;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

/**
 * @author zwh
 * @version 1.0.0
 * @description 模拟的@ConfigurationAnnotation配置类
 */
@Configuration
public class ConfigurationAnnotationConfig {
    @Bean
    public Person person(){
        return new Person();
    }
}
```