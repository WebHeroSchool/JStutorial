# JavaScript Style Guide 

## 1. Зарезервированные слова
Не используйте зарезервированные слова в качестве ключей объектов.

*Делай вот так 😍*
``` js
let superman = {
  defaults: { clark: 'kent' },
  hidden: true
};
```
*А не так 🤮*
``` js
let superman = {
  default: { clark: 'kent' },
  private: true
};
```
## 2. Понятные имена переменных и функций
Код легче читать, когда при написании используются понятные, описательные имена функций и переменных, отражающие их смысл. Имена функций - это глаголы. Имена переменных - существительные.

*Делай вот так 😍*
``` js
function toCube(num) {
    let result = num * num * num;
    return result;
}
```
*А не так 🤮*
``` js
function wr(a) {
    let b = a * a *a;
    return b;
}
```
## 3. Имена переменных на английском языке
Имена переменных и функций не нужно писать транслитом, необходимо использовать английский язык.

*Делай вот так 😍*
``` js
let house = {};
let name = '';
function editName(name) {
    //тело функции
}
```
*А не так 🤮*
``` js
let dom = {};
let imya = '';
function pravkaImeni(imya) {
    //тело функции
}
```

## 4. Точка с запятой
Каждое предложение должно отделяться точкой с запятой. Полагаться на автоматическую вставку точек с запятыми запрещается.

*Делай вот так 😍*
``` js
alert('Hello');
let person = {};
person.name = 'Valya';
```
*А не так 🤮*
``` js
alert('Hello')
let person = {}
person.name = 'Valya'
```

## 5. Не использовать var
Объявляйте все переменные с помощью const или let. По умолчанию используется const, за исключением случаев, кгда нужно переназначить переменную. Ключевое слово var не должно использоваться.

*Делай вот так 😍*
``` js
const five = 5;
function toCube(num) {
    let result = num * num * num;
    return result;
}
let fiveInCube = toCube(five);
```
*А не так 🤮*
``` js
var five = 5;
function toCube(num) {
    var result = num * num * num;
    return result;
}
var fiveInCube = toCube(five);
```

## 6. Используй одинарные кавычки, а не двойные.
Обычные строковые литералы ограничиваются одинарной кавычкой (''), а не двойной ("").

*Делай вот так 😍*
``` js
let person = {
    name: 'Valentina',
    surname: 'Demina',
    age: '24'
}
```
*А не так 🤮*
``` js
let person = {
    name: "Valentina",
    surname: "Demina",
    age: "24"
}
```
## 7. Скобки
Открывающая фигурная скобка располагается на той же строке. Перед скобкой пробел. Закрывающая скобка располагается на новой строке.

*Делай вот так 😍*
``` js
function edit(name, age) {
  if (age < 100) {
    // тело цикла
  }
}
```
*А не так 🤮*
``` js
function edit(name, age)
{
  if (age < 100) { /*тело цикла*/ }
}
```
## 8. Используй camelCase
Используйте camelCase для именования объектов, функций и переменных.

*Делай вот так 😍*
``` js
  let thisIsMyObject = {};
  function thisIsMyFunction() {};
  let user = new User({
    name: 'Valentina Demina'
  });
```
*А не так 🤮*
``` js
let OBJEcttsssss = {};
  let this_is_my_object = {};
  function c() {};
  let u = new user({
    name: 'Valentina Demina'
  });
```

## 9. Объявляйте переменные для 'for' вне циклов
 Цикл будет медленне работать, если ему придеться вычислять длинну массива, например, на каждой итерации. 

*Делай вот так 😍*
``` js
let names = ['Valentina','Max','Andrey','Marina'];
let all = names.length;
for(let i=0;i<all;i++){
  doSomeThingWith(names[i]);
}
```
*А не так 🤮*
``` js
let names = ['Valentina','Max','Andrey','Marina'];
for(let i = 0; i < names.length; i++){
  doSomeThingWith(names[i]);
}
```

## 10. Снижение числа глобальных переменных
Сведением количества глобальных переменных к минимуму, вы значительно снижаете шансы нежелательного взаимодействия с другими приложениями, виджетами или библиотеками

*Делай вот так 😍*
``` js
let DudeNameSpace = {  
   name : 'Jeffrey',  
   lastName : 'Way',  
   doSomething : function() {...}  
}  
console.log(DudeNameSpace.name);
```
*А не так 🤮*
``` js
let name = 'Jeffrey';  
let lastName = 'Way';  
  
function doSomething() {...}  
  
console.log(name);
```
