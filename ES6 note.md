
- 没有`let`
    - 内层变量可能会覆盖外层变量
    
    ```javascript
      var tmp = new Date();
      
      function f() {
        console.log(tmp);
        if (false) {
          var tmp = "hello world";
        }
      }
      
      f(); // undefined
    ```
  - 用来计数的循环变量泄露为全局变量
  
    ```javascript
      var s = 'hello';
      
      for (var i = 0; i < s.length; i++) {
        console.log(s[i]);
      }
      
      console.log(i); // 5
    ```
- 函数表达式写法更优

```javascript
// 函数声明语句
{
  let a = 'secret';
  function f() {
    return a;
  }
}

// 函数表达式
{
  let a = 'secret';
  let f = function () {
    return a;
  };
}
```