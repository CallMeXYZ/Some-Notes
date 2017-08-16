# Java 

---
- JMS AMQP MQTT
    - **JMS**
    Java Messaging Service
    two message transfer type : queue or topic  
    reply on java platform
    - **AMQP**
    Advanced Message Queueing Protocol
    multi-platform
    five transfer type : direct，fanout，topic，headers，system 
    - **MQTT**
    Message Queueing Telemetry Transport 
    low cpu occupied
    for small devices
- for java reference parameter ,u can design a new reference to the parameter
- load `xxx.properties` file? your can use 
-
```java
public class MybatisConfig {
    @Bean
    public PropertyPlaceholderConfigurer propertyPlaceholderConfigurer() {
        PropertyPlaceholderConfigurer propertyPlaceholderConfigurer = new PropertyPlaceholderConfigurer();
        propertyPlaceholderConfigurer.setLocation(new ClassPathResource("test.properties"));
        return propertyPlaceholderConfigurer;
    }
    public void test(@Value("${test.name}") String name){
    }
}
```
or simply use annotation
```java
@PropertySource("classpath:test.properties")
public class MybatisConfig {
    public void test(@Value("${test.name}") String name){
    }
```
-too much `@ComponentScan` result in multiple execution of `@Schedule` schedule tasks in spring.
- Obeject parameter of method   reset to a new handle wont change the value of the orignal one.For Integer and String, if you set its values(such as i=i+1),it wont change the orginal values too.(Maybe because every value-set equals to reset to a new handle)
# Mybatis 

---
## Note
- if the parameter is null then will pass `(NULL)` to database;
- return primary key
```xml
<insert id="addUser" useGeneratedKeys="true" keyProperty="resultId" keyColumn="id">
 ......
</insert>
```
- mybatis may return  result that reuse obejects when using like association.Then u will ecounter  circular referenced issues ($ref) using json tools.In FastJson u can use `JSON.toJSONString(obj, SerializerFeature.DisableCircularReferenceDetect);` or use global setting `JSON.DEFAULT_GENERATE_FEATURE |= SerializerFeature.DisableCircularReferenceDetect.getMask();`
- u cannot add any comment inside a sql statement!!!
-  pass date as parameter `add_time = #{record.addTime,jdbcType=TIMESTAMP}`
- for `%#{param}%` using `CONCAT('%','${param}','%' )`

# Spring 
---
## Note
 -  if u want to use `html` which is as a  static page, u may try this:
add `<mvc:annotation-driven/> <mvc:resources mapping="/static/**" location="/static/" />` to the `springmvcServlet.xml` and put all static resources like html pages into `/webapp/static` forder.Then just call `return "/static/test.html?param=test"` . 
 - for redirect ,do sth like this `return "redirect:/static/test.html?param=test"`
 - `@RestController` is for return Object which will be automatically transformed into `json`.Also u can return page by `return new ModelAndView("ur page name",'object name in jsp',object)`.
- when u want to pass a object to the server,u don't need to add any tag to the parameter.BUT mind that u should pass parameter like `?test=1&&name=2` rather than `?test.test=1&&test.name=2` and remove the `@RequestParam`
-  version 5.1.33 of MySQL JDBC driver , u has to specify the serverTimezone explicitly in the connection string.
jdbc:mysql://localhost/db?useUnicode=true&useJDBCCompliantTimezoneShift=true&useLegacyDatetimeCode=false&serverTimezone=UTC
- if u want to pass an object to the controller, u can simply remove the `@RequestParam` annotation. Pass an json or use A=?&B=? is OK
- how to set ur method return as JSON?
  use `@RestController` and `@RequestMapping("test")` or
  ` @RequestMapping(value = "/test", produces = "application/json")
    @ResponseBody`
- let controller return object not including null properties:
  add `@JsonInclude(Include.NON_NULL)` annotation to the specific modal
- `requestMaping("test")` may conflict with `addResourceHandler("/*.text")` when accessing `www.test.com/testproject/test`,both text file and controller with respond and got 406 error:` The resource identified by this request is only capable of generating responses with characteristics not acceptable according to the request "accept" headers.`
