# Integration Testing

## Definition
Integrating different components of an application and evaluating how they behave as a single, integrated entity is known as integration testing. It is crucial to check that the different parts are functioning effectively and appropriately interacting with one another after integration.

## Implementation
Below, you can see a simple implementation of integration testing by creating a HttpEntity that holds headers and sending a GET request with it. 

```java
    TestRestTemplate restTemplate = new TestRestTemplate();
    HttpHeaders headers = new HttpHeaders();

    @Test
    public void reposTest(){
        HttpEntity<String> entity = new HttpEntity<String>(null, headers);
        ResponseEntity<String> response = restTemplate.exchange("https://60a21d3f745cd70017576092.mockapi.io/api/v1/repos", HttpMethod.GET, entity, String.class);
        assertEquals( MediaType.APPLICATION_JSON, response.getHeaders().getContentType());
    }
```
## Setup
First, it is needed to add framework support for Spring framework and invalidate the project to utilize springboot. We also need to add necessary plugins and dependencies to our build.gradle file.
Plugins:
```
plugins{
    id 'org.springframework.boot' version '2.7.4'
    id 'io.spring.dependency-management' version '1.0.14.RELEASE'
}
```
Dependencies:
```
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    implementation 'net.thauvin.erik.httpstatus:httpstatus:1.0.5'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
}
```
gradlew should also be given execute permission:
```
chmod +x gradlew
```
## Testing
![image](https://user-images.githubusercontent.com/71690774/194756591-7e30a467-a583-4881-a011-00fac5df6efe.png)
![image](https://user-images.githubusercontent.com/71690774/194756625-367501c0-8ba9-4ac6-bc4e-aac3d917c31e.png)

All my three tests have success result
