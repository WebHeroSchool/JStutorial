# JavaScript Best Practice Guide

## 1. Называть переменные и функции просто, коротко и понятно
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
``` js
function increaseTheNumberThreeTimesAndReturnResultBack(number) {
    let resultOfThisFunction = number * number *number;
    return number;
}
```
## 2. Избегать глобальных переменных
Глобальные перменные и функции плохая идея, потому что скрипт добавленный позже может иметь переменные с такими же именами и в таком случае новый скрипт перепишет старые данные. 

*Делай вот так 😍*
``` js
var current = null;
function init(){...}
function change(){...}
function verify(){...}
```
*А не так 🤮*
``` js
var myNameSpace = {
  current:null,
  init:function(){...},
  change:function(){...},
  verify:function(){...}
}
```
## 3. Комментарии
Комментировать необходимо как для других разработчиков, так и для себя, так как можно не вспомнить подробностей и пояснения будут кстати. __Комментируй столько, сколько необходимо, но без фанатизма.__
Для комментирования нескольких строк текста используются /* */, которые необходимо ставить на отдельных строках. Если нужно закомментировать одну строку используй //.

*Делай вот так 😍*
``` js
module = function(){
  var current = null;
  function init(){
  };
/*
  function show(){
    current = 1;
  };
  function hide(){
    show();
  };
*/
  return{init:init,show:show,current:current}
}();
```
*А не так 🤮*
``` js
module = function(){
  var current = null;
  function init(){
  };
/* function show(){
    current = 1;
  };
  function hide(){
    show();
  }; */
  return{init:init,show:show,current:current}
}();
```
## 4. Лучше избегать смешивания с другими технологиями
Это возможно - сделать все необходимые изменения через JavaScript и DOM, но это не самая лучшая идея.Лучше создать класс с нужными стилями в файле style.css и в коде javascript добавилять нужный класс со стилями элементу.
Не все js-разработчики знакомы с CSS и для них будет сложнее понять код, который меняет еще и стили.

*Делай вот так 😍*
``` js
let button = document.getElementById('main-button');
button.className.add('red');
```
*А не так 🤮*
``` js
let button = document.getElementById('main-button');
button.style.padding = '20px';
button.style.background = 'red';
button.style.color = 'white';
button.style.fontWeight = 'bold';
}
```
## 5. Лучше использовать сокращенную запись 
Нужно смотреть по ситуации и сокращать запись там, где это имеет смысл, так как сократив слишком много код можно сделать нечетабельным. 

*Делай вот так 😍*
``` js
var cow = {
  colour:'brown',
  commonQuestion:'What now?',
  moo:function(){
    console.log('moo);
  },
  feet:4,
  accordingToLarson:'will take over the world'
};
```
``` js
var awesomeBands = [
  'Bad Religion',
  'Dropkick Murphys',
  'Flogging Molly',
  'Red Hot Chili Peppers',
  'Pornophonique'
];
```
*А не так 🤮*
``` js
var cow = new Object();
cow.colour = 'brown';
cow.commonQuestion = 'What now?';
cow.moo = function(){
  console.log('moo');
}
cow.feet = 4;
cow.accordingToLarson = 'will take over the world';
```
``` js
var awesomeBands = new Array();
awesomeBands[0] = 'Bad Religion';
awesomeBands[1] = 'Dropkick Murphys';
awesomeBands[2] = 'Flogging Molly';
awesomeBands[3] = 'Red Hot Chili Peppers';
awesomeBands[4] = 'Pornophonique';
```
## 6. Одна функция - одна задача
Это одна из главных хороших практик в программировании - убедись, что созданная функция выполняет только одну задачу, это сделает код понятнее и поможет найти ошибку в дальнейшем.
*Делай вот так 😍*
``` js
function createLink(text,url){
  var newLink = document.createElement('a');
  newLink.setAttribute('href',url);
  newLink.appendChild(document.createTextNode(text));
  return newLink;
}
function createMenu(){
  var menu = document.getElementById('menu');
  var items = [
    {t:'Home',u:'index.html'},
    {t:'Sales',u:'sales.html'},
    {t:'Contact',u:'contact.html'}
  ];
  for(var i=0;i<items.length;i++){
    var item = createLink(items.t,items.u);
    item.className = 'menu-item';
    menu.appendChild(item);
  }
}
```
*А не так 🤮*
``` js
function addLink(text,url,parentElement){
  var newLink = document.createElement('a');
  newLink.setAttribute('href',url);
  newLink.appendChild(document.createTextNode(text));
  if(parentElement.id === 'menu'){
    newLink.className = 'menu-item';
  }
  if(url.indexOf('mailto:')!==-1){
    newLink.className = 'mail';
  }
  parentElement.appendChild(newLink);
}
```
## 7. Лучше избегать многократного вложения
Вложение, которое объясняется логикой программы - удобная штука, однако чрезмерное вложение усложняет поддержку кода. 
Также есть проблема в переменных цикла, первую ты называешь i, а потом из-за сильной вложенности в ход идут j,k,l,n,m и код становится грязным, в нем легко запутаться.
*Делай вот так 😍*
``` js
function renderProfiles(o){
  var out = document.getElementById(‘profiles’);
  for(var i=0;i<o.members.length;i++){
    var ul = document.createElement(‘ul’);
    var li = document.createElement(‘li’);
    li.appendChild(document.createTextNode(data.members[i].name));
    li.appendChild(addMemberData(o.members[i]));
  } 
  out.appendChild(ul);
}
function addMemberData(member){
  var ul = document.createElement(‘ul’);
  for(var i=0;i<member.data.length;i++){
    var li = document.createElement(‘li’);
    li.appendChild(
      document.createTextNode(
        member.data[i].label + ‘ ‘ +
        member.data[i].value
      )
    );
  }
  ul.appendChild(li);
  return ul;
}
```
*А не так 🤮*
``` js
function renderProfiles(o){
  var out = document.getElementById(‘profiles’);
  for(var i=0;i<o.members.length;i++){
    var ul = document.createElement(‘ul’);
    var li = document.createElement(‘li’);
    li.appendChild(document.createTextNode(o.members[i].name));
    var nestedul = document.createElement(‘ul’);
    for(var j=0;j<o.members[i].data.length;j++){
      var datali = document.createElement(‘li’);
      datali.appendChild(
        document.createTextNode(
          o.members[i].data[j].label + ‘ ‘ +
          o.members[i].data[j].value
        )
      );
      nestedul.appendChild(datali);
    }
    li.appendChild(nestedul);
  } 
  out.appendChild(ul);
}
```
## 8. Оптимизировать циклы
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
## 9. Нельзя доверять каким-либо данным
Обязательно убедись, что все данные, которые ты используешь, представляют собой именно то, что тебе нужно. Это наиболее важно для данных, полученных через запрос.
*Делай вот так 😍*
``` js
function buildMemberList(members){
  if(typeof members === 'object' && 
     typeof members.slice === 'function'){
    var all = members.length;
    var ul = document.createElement('ul');
    for(var i=0;i<all;i++){
      var li = document.createElement('li');
      li.appendChild(document.createTextNode(members[i].name));
      ul.appendChild(li);
    }
    return ul;
  }
}
```
*А не так 🤮*
``` js
function buildMemberList(members){
  var all = members.length;
  var ul = document.createElement('ul');
  for(var i=0;i<all;i++){
    var li = document.createElement('li');
    li.appendChild(document.createTextNode(members[i].name));
    ul.appendChild(li);
  }
  return ul;
}
```
## 10. Точка с запятой
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
