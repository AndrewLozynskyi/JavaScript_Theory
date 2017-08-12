# Network

1) What are HTTP methods? List all HTTP methods that you know, and explain them.

- GET
	- The GET method requests a representation of the specified resource. Requests using GET should only retrieve data and should have no other effect.
- POST
	- The POST method requests that the server accept the entity enclosed in the request as a new subordinate of the web resource identified by the URI.
- HEAD
	- The HEAD method asks for a response identical to that of a GET request, but without the response body. This is useful for retrieving meta-information written in response headers, without having to transport the entire content.
- PUT
	- The PUT method requests that the enclosed entity be stored under the supplied URI.
- DELETE
	- The DELETE method deletes the specified resource.
- TRACE
	- The TRACE method echoes the received request so that a client can see what (if any) changes or additions have been made by intermediate servers.
- OPTIONS
	- The OPTIONS method returns the HTTP methods that the server supports for the specified URL.
- CONNECT
	- The CONNECT method converts the request connection to a transparent TCP/IP tunnel, usually to facilitate SSL-encrypted communication (HTTPS) through an unencrypted HTTP proxy.
- PATCH
	- The PATCH method applies partial modifications to a resource.

2) Difference between get and post

- GET - Requests data from a specified resource
- POST - Submits data to be processed to a specified resource

# HTML

# CSS

# JavaScript
1) Context ( this ) in js.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this

2) Functions call, apply, bind
http://getinstance.info/articles/javascript/call-apply-and-bind-functions/

3) Closures
https://developer.mozilla.org/uk/docs/Web/JavaScript/Closures

4) Hoisting
https://developer.mozilla.org/ru/docs/%D0%A1%D0%BB%D0%BE%D0%B2%D0%B0%D1%80%D1%8C/%D0%9F%D0%BE%D0%B4%D0%BD%D1%8F%D1%82%D0%B8%D0%B5

5) Difference between var, let, const.

const -- неможна переприсвоювати.
let неможна переоголошувати, а var можна.
let видимий тільки в тілі цилку, а var в цілій функції. 

  ```
  function exampleForLet() {
  	i - invisible here
  	for (let i = 0; i<10; i++){
  		i - visible here
  	}
  	i - invisible here
  }
  ```

  ```
  function exampleForVar() {
  	i - visible here
  	for (var i = 0; i<10; i++){
  		i - visible here
  	}
  	i - visible here
  }
  ```

6) Strict vs non-strict
https://learn.javascript.ru/strict-mode

7) Async js
https://habrahabr.ru/post/282477/

8) Promises
https://developer.mozilla.org/uk/docs/Web/JavaScript/Reference/Global_Objects/Promise

9) Two-way /one-way data binding
https://stackoverflow.com/questions/34519889/can-anyone-explain-the-difference-between-reacts-one-way-data-binding-and-angula

10) Algorithm complexity O(n), O(n^2), O(n*logn)

11) What are the primitive/native types exist?
https://stackoverflow.com/questions/16115512/understanding-javascript-immutable-variable

12) How to find an element from an array? How it internally works?
  ```
function findIndexByValue(arraytosearch, valuetosearch) {
 
	for (var i = 0; i < arraytosearch.length; i++) {
 
		if (arraytosearch[i] == valuetosearch) {
			return i;
		}
	}
		return null;
}
  ```

13) Recursion. How do get nth Fibonacci number?
  ```
function fibonacci(num) {
  if (num <= 1) return 1;

  return fibonacci(num - 1) + fibonacci(num - 2);
}
fibonacci(num);
```

14) Destructuring
https://learn.javascript.ru/destructuring

15) Recursion. print from 1 to n.
```
function printNumbers(n){
    var result;
    if(n <= 1)
        result = '1';
    else
        result = printNumbers(n-1) + n;
    console.log(result);
    return result;
}
printNumbers(n)
```

## Unit testing

## jQuery

- Explain "chaining"
- Explain "deferreds"
- Name 4 different values you can pass to the jQuery method
- What is the difference between .get(), [], and .eq()
- What is the difference between .bind(), .live(), and .delegate()
- Optimize this selector: $(".foo div#bar:eq(0)")
- How can I select 20th div with jQuery?

## Angular specific questions

- Component vs directive
- Factory vs service vs provider
- Digest cycle
- Why use $timeout and not setTimeout
- Data sharing between controllers ($rootScope, eventEmiter, service)
- Difference between ng-if and ng-show?
- Dependency injection?
- ng-bind
- UI router
- ng-app during dom load

## ES6

https://github.com/lukehoban/es6features

## React / Redux

- Why React? What is the key feature?
- Virtual DOM?
- stateless component?
- testing?

# DB 
1) Які існують ключі в БВ
 - Первинні і вторинні.
 - Первинний ключ — це одне або кілька полів (стовпців), комбінація значень яких однозначно визначає кожний запис у таблиці. Первинний ключ не допускає значень Null і завжди повинен мати унікальний індекс. Первинний ключ використовується для зв’язування таблиці з зовнішніми ключами в інших таблицях.
 - Вторинний ключ — це одне або кілька полів (стовпців) у таблиці, що містять посилання на поле або поля первинного ключа в іншій таблиці. Зовнішній ключ визначає спосіб об’єднання таблиць.
2) Типи звязків в БД.
 - Зв’язок "один-до-багатьох"
 - Зв’язок "багато-до-багатьох"
 - Зв’язок "один-до-одного"
3) Запити

# OOP
1) How can you declare a class in Javascript?
- using function as a constructor

  ```
  function Person(name) { this.name = name }
  var person = new Person("Rafael");
  person.name; // "Rafael"
  ```

- Class Literal notation

  ```
  var person = {  
      name: "",
      setName: function(name) {
          this.name = name;
      }
  }
  person.setName("Rafael");  
  person.name; // "Rafael"
  ```

- Singleton through a function

  ```
  var person = new function() {  
      this.setName = function(name) {
          this.name = name;
      }
      this.sayHi = function() {
          return "Hi, my name is " + this.name;
      }
  }
  person.setName("Rafael");  
  alert(person.sayHi()); // Hi, my name is Rafael 
  ```
- Constructors
https://developer.mozilla.org/uk/docs/Web/JavaScript/Reference/Global_Objects/Object/constructor
- Prototypes
https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype
- What is **encapsulation**? *(Packing of data and functions into a single component)*
Інкапсуляція - Способ комплектации данных и методов, которые используют данные.
- What is **polymorphism**? *(Variable of type Shape could refer to an object of type Square, Circle... Ability of a function to handle objects of many types)*
Поліморфізм - Различные классы могут объявить один и тот же метод или свойство.
- **Inheritance**
Наслідування - Класс может наследовать характеристики от другого класса.
https://developer.mozilla.org/ru/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript

# Design Patterns



