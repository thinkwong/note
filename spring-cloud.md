

## Spring Cloud Zuul

面向服务的路由：让路由的 path 不是映射具体的 url，而是让它映射到某个具体的服务，而具体的 url 则交给 Eureka 的服务发现机制去自动维护，我们称这类路由为面向服务的路由。

spring cloud 超时设置：

```
spring.cloud.loadbalancer.retry.enabled=true
ribbon.ReadTimeout=60000
ribbon.ConnectTimeout=60000
```
