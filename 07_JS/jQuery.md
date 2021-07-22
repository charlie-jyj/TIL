# jQuery 



## Attributes



## Selectors



## Events



#### .on()

```
.on(events[,selector][,data],handler)
```

1.7 버전부터 추가되었고 기존의 bind, live, delegate 는 사용하지 않는다.

단, click 함수는 on 함수의 숏컷 버전으로 남아있다.



- 예제

```javascript
$( "#dataTable tbody tr" ).on( "click", function() {
  console.log( $( this ).text() );
});

$( "#dataTable tbody" ).on( "click", "tr", function() {
  console.log( $( this ).text() );
});

function notify() {
  alert( "clicked" );
}
$( "button" ).on( "click", notify );
```





#### .click()



- javascript

```javascript
document.querySelector("#id").addEventListener('click', function(event){
    // event 함수 내용
})
```



- 예제

```javascript
$( "#target" ).click(function() {
  alert( "Handler for .click() called." );
});
```





#### .trigger()

```
.trigger(eventType[,extraParameters])
```





- javascript

```javascript
let elem = document.querySelector("#id");
elem.click();
```



```javascript
const event = new Event('build');

// Listen for the event.
elem.addEventListener('build', function (e) { /* ... */ }, false);

// Dispatch the event.
elem.dispatchEvent(event);
```



- old-fashioned

```javascript
// Create the event.
const event = document.createEvent('Event');

// Define that the event name is 'build'.
event.initEvent('build', true, true);

// Listen for the event.
elem.addEventListener('build', function (e) {
  // e.target matches elem
}, false);

// target can be any Element or other EventTarget.
elem.dispatchEvent(event);
```





- 예제

```javascript
$( "#foo" ).on( "click", function() {
  alert( $( this ).text() );
});
$( "#foo" ).trigger( "click" );
```





## CSS



### .css()

```
.css(propertyName)
Type: String

.css(propertyNames)
Type: Array

```



- javascript

```
let button = document.querySelector(".classname");
button.style.color = "black";
```

