---
title: 나는 아래 결과에 대해서 아직 이해못하겠다
description: 1번 예제
date: ''
categories: []
keywords: []
slug: ''
---

1번 예제

function Person(firstname, lastname)  
{  
  var fullName = firstname + " " + lastname;

  this.getFirstName = function () { return firstname; };  
  this.getLastName = function () { return lastname; };  
  this.getFullName = function () { return fullName; };  
}  
  
var aPerson = new Person ("John", "Smith");

aPerson.firstname = "Penny";  
aPerson.lastname = "Andrews";  
aPerson.fullName = "Penny Andrews";

console.log(aPerson);  
console.log(aPerson.getFirstName());  
console.log(aPerson.getLastName());  
console.log(aPerson.getFullName());

\----------------------------------------------------------------  
\[결과\]

Person {  
  getFirstName: \[Function\],  
  getLastName: \[Function\],  
  getFullName: \[Function\],  
  firstname: 'Penny',  
  lastname: 'Andrews',  
  fullName: 'Penny Andrews' }

John  
Smith  
John Smith

  

2번 예제

function Person(firstname, lastname)  
{  
  var fullName = firstname + " " + lastname;  
}  
Person.prototype.getFirstName = function () { return this.firstname; };  
Person.prototype.getLastName = function () { return this.lastname; };  
Person.prototype.getFullName = function () { return this.fullName; };  
var aPerson = new Person ("John", "Smith");

aPerson.firstname = "Penny";  
aPerson.lastname = "Andrews";  
aPerson.fullName = "Penny Andrews";

console.log(aPerson);  
console.log(aPerson.getFirstName());  
console.log(aPerson.getLastName());  
console.log(aPerson.getFullName());

\----------------------------------------------------------------  
\[결과\]

Person {  
  firstname: 'Penny',  
  lastname: 'Andrews',  
  fullName: 'Penny Andrews' }

Penny  
Andrews  
Penny Andrews