# Network

1) What are HTTP methods? List all HTTP methods that you know, and explain them.
- HTTP - (Hyper Text Transfer Protocol) - протокол передачі даних.
- OPTIONS
	- Цей метод може служити для визначення можливостей веб-сервера.
- GET
	- Запрошує вміст вказаного ресурсу.
- HEAD
	- Аналогічний методу GET, за винятком того, що у відповіді сервера відсутнє тіло. Це корисно для витягання мета-інформації, заданої в заголовках відповіді, без пересилання всього вмісту. 
- POST
	- Передає призначені для користувача дані заданому ресурсу. 
- PUT
	- Завантажує вказаний ресурс на сервер.
- PATCH
	- Завантажує певну частину ресурсу на сервер.
- DELETE
	- Видаляє вказаний ресурс.
- TRACE
	- Повертає отриманий запит так, що клієнт може побачити, що проміжні сервери додають або змінюють в запиті.
- CONNECT
	- Для використання разом з проксі-серверами, які можуть динамічно перемикатися в тунельний режим SSL.

# HTML
- https://career.guru99.com/top-50-html-interview-questions/
- https://www.codeproject.com/Articles/702051/important-HTML-Interview-questions-with-answe
# CSS
- https://career.guru99.com/top-50-csscascading-style-sheet-interview-questions/
- http://www.skilledup.com/articles/25-css-interview-questions-answers
- https://career.guru99.com/top-17-sass-interview-questions/

# JavaScript
- https://career.guru99.com/top-85-javascript-interview-questions/
- https://github.com/nishant8BITS/123-Essential-JavaScript-Interview-Question

1) Context ( this ) in js.
- 'this' відноситься до об'єкта, з якого він був викликаний.
- В глобальному контексті this зсилається на глобальний обєкт незалжно чи строгий чи не строгий режим.
```
console.log(this === window); // true
```
- В межах функції значення this залежить від того, як викликається функція -- залежить від "use strict".
```
function f1(){
  return this;
}
f1() // window
```
```
function f2(){
  "use strict"; // see strict mode
  return this;
}
f2() // undefined;
```
Для того щоб передати значення this від одного кoнтекста віншому треба викристати call або apply

- В стрілочних функціях this привязане до середовища в якому була створена функція.
```
var globalObject = this;
var foo = (() => this);
console.log(foo() === globalObject); // true
```
- В методі обєкта
Коли функція викликається як метод обєкта, this прикймає значення обєкта відносно якого викликається метод.
```
var o = {
  prop: 37,
  f: function() {
    return this.prop;
  }
};
console.log(o.f()); // logs 37
``` 
- this в цепочці objects prototype
```
var o = {
	f:function(){ 
		return this.a + this.b; 
	}
};
var p = Object.create(o);
p.a = 1;
p.b = 4;

console.log(p.f()); // 5
``` 
- В конструкторі === Коли функція викристовується як конструкторі(з ключовим словом new), this звязаний з новим створенним обєктом.
```
function C(){
  this.a = 37;
}

var o = new C();
console.log(o.a); // logs 37
``` 
- call and apply
```
function add(c, d){
  return this.a + this.b + c + d;
}
var o = {a:1, b:3};

add.call(o, 5, 7); // 1 + 3 + 5 + 7 = 16

add.apply(o, [10, 20]); // 1 + 3 + 10 + 20 = 34
``` 

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this

2) Functions call, apply, bind
- call and apply, bind дозволяє встановити значення this для функції.

- сall 
```
func.call(context, arg1, arg2, ...); // context = this
``` 
```
var user = {
  firstName: "Василий",
  surname: "Петров",
  patronym: "Иванович"
};

function showFullName(firstPart, lastPart) {
  alert( this.firstPart + " " + this.lastPart );
}

// f.call(контекст, аргумент1, аргумент2, ...)
showFullName.call(user, 'firstName', 'surname') // "Василий Петров"
showFullName.call(user, 'firstName', 'patronym') // "Василий Иванович"
``` 
- apply 

```
func.apply(context, [arg1, arg2, ...]); // context = this
``` 
-- bind
bind() дозволяє нам вказати силку обєкт зі значенням this, коли функція буде викликана.
```
var users = {
  data: [
      {name: 'John Smith'},
      {name: 'Ellen Simons'}
  ],

   showFirst: function (event) {
       console.log(this.data[0].name);
   }
}
 
$('button').click(users.showFirst); // this.data is undefined
$("button").click(users.showFirst.bind(users));
``` 
http://getinstance.info/articles/javascript/call-apply-and-bind-functions/

3) Closures
- Замикання -- це функції, які памятають середовище, в якому вони були створені. (область видимості функцій, змінних,...)

```
function init() {
  var name = "Mozilla"; // name is a local variable created by init
  function displayName() { // displayName() is the inner function, a closure
    alert(name); // use variable declared in the parent function    
  }
  displayName();    
}
init();// Mozilla
``` 
https://developer.mozilla.org/uk/docs/Web/JavaScript/Closures

4) Hoisting
https://developer.mozilla.org/ru/docs/%D0%A1%D0%BB%D0%BE%D0%B2%D0%B0%D1%80%D1%8C/%D0%9F%D0%BE%D0%B4%D0%BD%D1%8F%D1%82%D0%B8%D0%B5
```
var x = 1; // Инициализируем x
console.log(x + " " + y);  // y - undefined
var y = 2;
//код выше и код ниже одинаковые

var x = 1; // Инициализируем x
var y; // Объявляем y
console.log(x + " " + y);  // y - undefined
y = 2; // Инициализируем y
``` 


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
```
async function throwsValue() {
    throw new Error('oops');
}
throwsValue()
    .then((resolve) => {
            console.log("resolve:" + resolve);
        },
        (reject) => {
            console.log("reject:" + reject);
        });
//prints "reject:Error: oops"
 ```

8) Promises
https://developer.mozilla.org/uk/docs/Web/JavaScript/Reference/Global_Objects/Promise
```
// Создаётся объект promise
let promise = new Promise((resolve, reject) => {

  setTimeout(() => {
    // переведёт промис в состояние fulfilled с результатом "result"
    resolve("result");
  }, 1000);

});

// promise.then навешивает обработчики на успешный результат или ошибку
promise
  .then(
    result => {
      // первая функция-обработчик - запустится при вызове resolve
      alert("Fulfilled: " + result); // result - аргумент resolve
    },
    error => {
      // вторая функция - запустится при вызове reject
      alert("Rejected: " + error); // error - аргумент reject
    }
  );
 ```

9) Two-way /one-way data binding
https://stackoverflow.com/questions/34519889/can-anyone-explain-the-difference-between-reacts-one-way-data-binding-and-angula
- фішка ангулара -- в One-way view не одновляється автоматично, треба писати код для оновлення данний в вюшці. В Two-way View апдейтиться автоматично.

10) Algorithm complexity O(n), O(n^2), O(n*logn)

- Швидкість алгоритму
- O(n) - найти елемент в масиві 
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
- O(n2) -- 2 цикли в функції (бульбашковий алгоритм)
```
function BubbleSort(A) {
	var n = a.length - 1;
	for ( var i = 0; i < n; i++ ) {
		for ( var j = 0; j < n - i; j++ ) {
			if ( A[j] > A[j+1] ) {
				var t = A[j];
				A[j] = A[j+1];
				A[j+1] = t;
			}
		}
	}
}
BubbleSort([3,5,2,1,7]);
```
- O(log n)
```
function BinarySearch(t, A){
	var i = 0;
	var j = A.length-1;
	var k;
	while (i <= j) {
		k = Math.floor((i+j)/2);
		if ( t === A[k] ){
			return k;
		} else if ( t < A[k] ) {
			j = k - 1;
		} else { 
			i = k + 1; 
		}
	}
	return false;
}

Binary Search(3, [1,2,3,4,5,6,7,8,9])
```

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

13.1) quikSort algoritm
```
function quicksort(array) {
  if (array.length <= 1) {
    return array;
  }

  var pivot = array[0];
  
  var left = []; 
  var right = [];

  for (var i = 1; i < array.length; i++) {
    array[i] < pivot ? left.push(array[i]) : right.push(array[i]);
  }

  return quicksort(left).concat(pivot, quicksort(right));
};

var unsorted = [23, 45, 16, 37, 3, 99, 22];
var sorted = quicksort(unsorted);

console.log(sorted)
```

14) Destructuring
https://learn.javascript.ru/destructuring

15) Recursion. print from 1 to n.
```
function printNumbers(n){
    var result;
    if(n <= 1) {
        result = '1';
    }
    else{
        result = printNumbers(n-1) + n;
    }
    //console.log(result);
    return result;
}
printNumbers(n)
```
16) Binaty search
```
function some(array, targetValue) {
    var min = 0;
    var max = array.length - 1;
    var guess;

    while(min <= max) {
        guess = Math.floor((max + min) / 2);

        if (array[guess] === targetValue) {
            return guess;
        }
        else if (array[guess] < targetValue) {
            min = guess + 1;
        }
        else {
            max = guess - 1;
        }

    }

    return -1;
}
some([1,2,3,4,5,6,7,8,9,10], 2); // 1
```
17) Base algirithm
http://www.thatjsdude.com/interview/js1.html

## Unit testing
https://www.smashingmagazine.com/2012/06/introduction-to-javascript-unit-testing/
## jQuery

- Explain "chaining"
- Explain "deferreds"
- Name 4 different values you can pass to the jQuery method
- What is the difference between .get(), [], and .eq()
- What is the difference between .bind(), .live(), and .delegate()
- Optimize this selector: $(".foo div#bar:eq(0)")
- How can I select 20th div with jQuery?

- https://www.toptal.com/jquery/interview-questions
- https://www.tutorialspoint.com/jquery/jquery_interview_questions.htm
- https://career.guru99.com/top-50-jquery-interview-questions/

```
$("button").click(function(){
    $.get("demo_test.asp", function(data, status){
        alert("Data: " + data + "\nStatus: " + status);
    });
});
$("button").click(function(){
    $.post("demo_test_post.asp",
    {
        name: "Donald Duck",
        city: "Duckburg"
    },
    function(data, status){
        alert("Data: " + data + "\nStatus: " + status);
    });
});
```

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

- https://www.codementor.io/angularjs/tutorial/angularjs-interview-questions-sample-answers
- http://www.c-sharpcorner.com/article/top-50-angularjs-interview-questions-and-answers/
- https://career.guru99.com/top-25-angular-js-interview-questions/


## ES6

https://github.com/lukehoban/es6features

## React / Redux

- Why React? What is the key feature?
- Virtual DOM?
- stateless component?
- testing?

- https://tylermcginnis.com/react-interview-questions/
- https://www.codementor.io/reactjs/tutorial/5-essential-reactjs-interview-questions

# DB 
- https://www.guru99.com/mongodb-interview-questions.html
- https://career.guru99.com/top-50-mysql-interview-questions-answers/
1) Які існують ключі в БВ
 - Первинні і вторинні.
 - Первинний ключ — це одне або кілька полів (стовпців), комбінація значень яких однозначно визначає кожний запис у таблиці. Первинний ключ не допускає значень Null і завжди повинен мати унікальний індекс. Первинний ключ використовується для зв’язування таблиці з зовнішніми ключами в інших таблицях.
 - Вторинний ключ — це одне або кілька полів (стовпців) у таблиці, що містять посилання на поле або поля первинного ключа в іншій таблиці. Зовнішній ключ визначає спосіб об’єднання таблиць.
2) Типи звязків в БД.
 - Зв’язок "один-до-багатьох"
 - Зв’язок "багато-до-багатьох"
 - Зв’язок "один-до-одного"
3) Запити
http://bestwebit.biz.ua/w3c_1/sql.php
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
- Інкапсуляція – механізм, який поєднує дані та методи, що обробляють ці дані і захищає і те і інше від зовнішнього впливу або не вірного використання. Коли і методи і данні об’єднуються таким чином — створюється об’єкт.

- Поліморфізм – властивість, яка дозволяє одне і те саме ім’я використовувати для вирішення декількох технічно різних задач.

- Наслідування – процес, завдяки якому один об’єкт може придбати властивості іншого, тобто наслідувати властивість іншого обєкту і додавати риси характерні тільки для нього самого.

https://developer.mozilla.org/ru/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript

# Design Patterns
- http://www.tutorialspoint.com/design_pattern/design_pattern_interview_questions.htm


https://github.com/MaximAbramchuck/awesome-interview-questions/blob/master/README.md#database-technologies