# HTML &CSS
---
## Note 

- **Hyper Text Markup Language**
- url **Uniform Resource Locator**
- block element will add a line automatically after itself, like `<h>`,`<p>` 
- fuck mind the ` : `  and ` ：` , sometimes it drives u crazy like a shit. 
- the default height of body and html is `height: auto`,so if u set `height: 100%` in a div it doesn't help.Add the same attribute to both html and body too.
## Issue
- nested frame in `frameset` use `noresize="noresize"` in child will result in the same effect int parent;
- remember to set both `html` and `body` `heihgt:100%,width:100%;`,if u want add percentage size of an element.
- line-height when using percentage is pecentage of initial font size!!!!if using px then right 
```
 div:before {
  content: "";
  display: inline-block;
  height: 100%;
  vertical-align: middle;
}
```
- it seems that `background-size: cover` is not enough for fullscreen background, add `background-attachment: fixed` will work.
- sometimes u can do wonderful thing by setting background such as when u want to draw a line through out the whole  timeline 
- quot nesting use `\'` or `\"`
- img sr had bettter start with 'http://'
- not first child?
- adminlte `app.min.js` will affect some input-interaction such as click box head to collapse if u set `data-widget='collapse'` to the box header without do anything else derectly.
- `<img>` has the initial style of `diplay` as `inline`,when u want to center,add `display:block`
- how to keep a div to be square while it has a percentage width?
```css
container {
    width:'100%',
    padding-bottom:'100%'
    //just keep the two percentage as the same
}
container > child {
  position: absolute;
  top: 0; bottom: 0; left: 0; right: 0;
}
```
```html
<div style={{position:'relative',display:'inline-block',width:'25%',paddingBottom:'25%'}}>
    <div style={{position:'absolute',top:'0',right:0,bottom:0,left:0,padding:'5px'}}>
    <img style={{height:'100%',width:'100%'}} src={this.props.url}/>
     </div>
</div>
```
- left div responsive width,right take the rest 
```
.left{
    display:table-cell,
    white-wrap:nowrap
}
.right{
    display:table-cell,
    white-wrap:nowrap
}
```
- when using rem to get responsive page,dont change tiny px such as  the border size  (1px) to rem,u may get <1px result and never show
- child `div` with `margin-top` attribute will make its parent has the same effect too (transit down),just add `overflow:hidden` to the parent. 
- Fill remaining vertical space,u can use flex or table
```html
<div id="wrapper">
    <div id="first" class="row">
        <div class="cell"></div>
    </div>
    <div id="second" class="row">
        <div class="cell"></div>
    </div>
</div>
```
```css
#wrapper
{
   width:300px;
   height:100%;
   display:table;
}

.row 
{
   display:table-row;
}

.cell 
{
   display:table-cell;
}

#first .cell
{
   height:200px;
   background-color:#F5DEB3;
}

#second .cell
{
   background-color:#9ACD32;
}
```
- the container need to hack to contain its float children,use `.clearfix` to help: [Link][1] 
```css
.clearfix:before, .clearfix:after 
{ content: ""; 
  display: table; 
}
```
- vertical center see [Link][2]
#JS
---
##Note
-  re-declare a variable will not recreate , the value of it persists.
-  if u set a value to a undecalred var then it will become global var, whether inner a function or not.
- what fu! `5=='5'` is true while `5==='5'` is truly false.
- constructor? what f! funny
```javascript
function person1(firstnamer)
{
	this.firstname=firstname;
	this.changeName=changeName;
	function changeName(name)
	{
	this.firstnamer=name;
	}
}
function person2(firstnamer)
{
	this.firstname=firstname;
	this.changeName=
	function (name)
	{
	this.firstnamer=name;
	}
}
function personERROR(firstnamer)
{
	this.firstname=firstname;
	function changeName(name)
	{
	this.firstnamer=name;
	}
```


```
var myFather=new person("Bill");
myFather.changeName("Gates");
``` 
- u can add customised attribute
- get parameter from url 
```javascript
function getUrlParameter(sParam) {
    var sPageURL = decodeURIComponent(window.location.search.substring(1)),
        sURLVariables = sPageURL.split('&'),
        sParameterName,
        i;

    for (i = 0; i < sURLVariables.length; i++) {
        sParameterName = sURLVariables[i].split('=');

        if (sParameterName[0] === sParam) {
            return sParameterName[1] === undefined ? true : sParameterName[1];
        }
    }
};
```
- ajax upload file use `FormData` 
```javascript
var formData = new FormData();
        $.each($("input[id=***]").get("0").files, function(i, file) {
            formData.append('files', file);
        });
        $.ajax({
            url: url,
            data: formData,
            type: "POST",
            async: false,
            enctype: 'multipart/form-data',
            contentType: false,
            processData: false, success: function (data) {
                console.log(data);
            }, error: function (e) {
                console.log(e);
            }
        });
```
-   `onclick=urFucntion(event)`  `event.stopPropagation();`
-   don't do sth like `<script src=''/>` use `<script> </script>` fully
-   formdata add object
```javascript
  $.each($("input[id=add_record_photos]").get("0").files, function(i, file) {
        formData.append('files', file);
    });
    for ( var key in result ) {
        formData.append(key, result[key]);
    }
```
```java
      public ResultCode method(MultipartFile[] files,UrObject log) {}
```
- if u want call `this` of the root function inside a `forEach()` function, u should pass this as the second param like  
```javascript
array.data.forEach(function(){
    ...
},this)
```
- use '[]' to assign object's attribute whose name is a varible
```javascript
 let a = 'test';
 //equals to `let b = {test:1}`
 let b = {[a]:1};
```
- `fetch` cannot send cookies by default so you cannot send request when the spring security is configured.Add`credentials: 'same-origin'`to its init config.
- singleton for js
```javascript
class TestClass {
 constructor() {
        this.test = 1;
    }

    test = ()=>this.test+=1
}
export const Test=new TestClass()
```
- `window.onclick` did not work on IE8,`document.onclick` is preferred
-  best `addEventListener` 
```javascript
if (!document.addEventListener && document.attachEvent) {
//ie 6 thru 10 
    document.attachEvent('ontouchstart', this.handleTouchOutside);
} else {
    document.addEventListener('touchstart', this.handleTouchOutside);
}
```
##Issues
- `setTimeOut(funcName,20);`OK
`setTimeOut(funcName(),20);` Maximum Call Stack Size Exceeded
`setTimeOut("funcName()",20);` OK
`setTimeOut(function(){funcName();},20);` OK
- background-color cannot set size
#JQuery
---
##Note
- No need to pass `this` as a parameter to a function, u can use `$(this)` directly.
- event.target vs. this. the former is the element which is clicked while the latter the element  which is registered the click function.
- pass parameters to click function
```javascript
// say your selector and click handler looks something like this...
$("some selector").click({param1: "Hello", param2: "World"}, cool_function);

// in your function, just grab the event object and go crazy...
function cool_function(event){
    alert(event.data.param1);
    alert(event.data.param2);
}
```
- **using `$('input').val()' must note that u have also set the radio value to null**
- `$(selector).eq(i)` return jquery object while `$(selector)[i]` or `$(selector).get[i]` return DOM object


#React
---
##Note
- cannot get `ref` of a arrow function component
- click outside to hide some element,use `onBlur` and set element 'tabIndex=-1'
#Tomcat
---
##Note
- if u got Garbled issues and could not find any solutions maybe u should just set ur tomcat config `<Connector port="8080" protocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8443" URIEncoding="UTF-8" />`


  [1]: http://stackoverflow.com/questions/8933494/bootstrap-css-containerbefore-display-table
  [2]: http://stackoverflow.com/questions/396145/how-to-vertically-center-a-div-for-all-browsers
