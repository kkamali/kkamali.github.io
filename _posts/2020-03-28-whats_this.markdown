---
layout: post
title:      "What's this?"
date:       2020-03-28 14:46:59 -0400
permalink:  whats_this
---


[Obligatory song link](https://www.youtube.com/watch?v=QLvvkTbHjHI)

"This" is probably the worst thing to describe when it comes to programming. It's like coding's own tongue twister. There doesn't seem to be a good way to describe "this" without sounding slightly unhinged and stumbling over your words. 

My first experience with the dreaded "this" comes from basic objects. 



```
const cat = {
  breed: 'munchkin', 
	name: 'Merry',
	introduce: function() {
	  console.log(`Hi, I'm ${this.name}, I'm a ${this.breed} cat`);
	}
}
```

When you call `cat.introduce()` it will print out `Hi I'm Merry, I'm a munchkin cat`. It's quite clear in this example "this" is referring to the cat object. So we can easily deduce that "this" gets its identity from what it was called on. 

Creating an introduce function outside of the cat object...

```
function introduce() {
  console.log(`Hi, I'm ${this.name}, I'm a ${this.breed} cat`);
}

introduce();
```
and calling it,  the console now prints out `Hi, I'm undefined, I'm a undefined cat`, what is `this` now? It's no longer a method on an object. Adding name and breed global variables, it will stop logging undefined. "This" without something calling it has the window as its scope! However... if we have the function like this...

```
function introductions() {
  name = "Pippin" ;
  breed = "munchkin";
  console.log(`Hi I'm ${this.name}, I'm a ${this.breed} cat`);
}

```

It will print out `Hi I'm Pippin, I'm a munchkin cat` -- this shouldn't be a surprise since functions in Javascript are objects. 

Looking at arrow functions (the latest Javascript phase) adds a little more complexity. Arrow functions don't have a context! According to MDN they use "lexical scope". With regular function invocations we look to the left to find out what `this` is, since they define `this` as soon as they're called. To dive deeper, if we replaced the cat object code with

```
const cat = {
  name: 'Merry', 
  breed: 'munchkin', 
  introduce: () => console.log(`Hi I'm ${this.name}, I'm a ${this.breed} cat`)
}
```

And call `cat.introduce()`, we'll get `undefined`s again! We no longer have the cat context, even though we're calling it directly on cat -- instead we just have the function scope and since `this` follows lexical scope, it will go up the chain until it reaches the window scope. 


```
function Person(){
  this.age = 0;

  setInterval(() => {
    this.age++;
  }, 1000);
}

var p = new Person();
```

We can see why `this` won't return undefined, it is able to get the scope since it's enclosed in a function! Which brings us to a new fun rule that I posit, before choosing an arrow function -- always be Jack Skellington. And ask "what's this?" 
