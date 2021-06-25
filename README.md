# spring-boot-oauth2.0-client
Demo project for Spring Boot and OAuth2.0 client


## Usage

This application uses the following OAuth2.0 dependency to run as client:

```
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-oauth2-client</artifactId>
</dependency>
```

This application has an additional dependency:
1. This application communicates with a Keycloak Authorization server running on port 8080, here are the instructions to configure it [Keycloak configuration](https://claudiocifuentes.atlassian.net/l/c/sESWWPFW).

application.properties file:
```
server.port=8087

spring.security.oauth2.client.registration.mywebclient.client-id = photos-web-client
spring.security.oauth2.client.registration.mywebclient.client-secret = 18846375-b63f-4cfd-94de-a7b3a1b6994a
spring.security.oauth2.client.registration.mywebclient.scope = openid, profile, roles
spring.security.oauth2.client.registration.mywebclient.authorization-grant-type = authorization_code
spring.security.oauth2.client.registration.mywebclient.redirect-uri = http://localhost:8087/login/oauth2/code/mywebclient

spring.security.oauth2.client.provider.mywebclient.authorization-uri = http://localhost:8080/auth/realms/appsclaudio/protocol/openid-connect/auth
spring.security.oauth2.client.provider.mywebclient.token-uri = http://localhost:8080/auth/realms/appsclaudio/protocol/openid-connect/token
spring.security.oauth2.client.provider.mywebclient.jwk-set-uri = http://localhost:8080/auth/realms/appsclaudio/protocol/openid-connect/certs
spring.security.oauth2.client.provider.mywebclient.user-info-uri = http://localhost:8080/auth/realms/appsclaudio/protocol/openid-connect/userinfo
spring.security.oauth2.client.provider.mywebclient.user-name-attribute = preferred_username
```

To run this application:

```
mvn spring-boot:run
```