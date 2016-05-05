#Spring#

----
 *  if u want to use `html` which is as a  static page, u may try this:
add `<mvc:annotation-driven/> <mvc:resources mapping="/static/**" location="/static/" />` to the `springmvcServlet.xml` and put all static resources like html pages into `/webapp/static` forder.Then just call `return "/static/test.html?param=test"` . 
 * for redirect ,do sth like this `return "redirect:/static/test.html?param=test"`
 * `@RestController` is for return Object which will be automatically transformed into `json`.Also u can return page by `return new ModelAndView("ur page name",'object name in jsp',object)`.
	
```java
int i = 0;
int j = i+1;
```