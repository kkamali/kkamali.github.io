---
layout: post
title:      "What's this?"
date:       2020-03-28 18:46:58 +0000
permalink:  whats_this
---


[Obligatory song link](https://www.youtube.com/watch?v=QLvvkTbHjHI)

"This" is probably the worst thing to describe when it comes to programming. It's like coding's own tongue twister. There doesn't seem to be a good way to describe "this" without sounding slightly unhinged and stumbling over your words. 

My first experience with the dreaded "this" comes from basic objects. 



```
const cat = {
  breed: 'munchkin', 
	name: 'Merry'
	introduce: function() {
	  console.log(`Hi, I'm ${this.name}, I'm a ${this.breed} cat`)
	}
}
```

When you call `cat.introduce()` it will print out `Hi I'm Merry, I'm a munchkin cat`. It's quite clear in this example "this" is referring to the cat object. So we can easily deduce that "this" gets its identity from what it was called on. 

If we pulled out the introduce function out of the object and called it, it will print to the console `Hi, I'm undefined, I'm a undefined cat`, what context is "this" now? It's no longer a method on an object. Adding name and breed variables (as global variables), it will stop logging undefined. "This" without something calling it has the window as its scope! However... if we have the function like this...

```
function introductions() {
  name = "Pippin" 
  breed = "munchkin"
  console.log(`Hi I'm ${this.name}, I'm a ${this.breed} cat`)
}

```

It will print out `Hi I'm Pippin, I'm a munchkin cat` -- this shouldn't be a surprise since functions in Javascript are objects. 

So arrow functions don't have a context. According to MDN they use "lexical scope". If we replaced the cat object code with
```
const cat = {
  name: 'Merry', 
  breed: 'munchkin', 
  introduce: () => console.log(`Hi I'm ${this.name}, I'm a ${this.breed} cat`)
}
```

And call `cat.introduce()`, we'll get undefineds again! We no longer have the cat context, even though we're calling it directly on cat -- instead we just have the function scope, and from there it would look at the window scope. MDN does say arrow functions aren't good for method calls -- and this would be why! 

Taking the example from MDN

```
function Person(){
  this.age = 0;

  setInterval(() => {
    this.age++;
  }, 1000);
}

var p = new Person();
```

We can see why "this" won't return undefined, it is able to get the scope since it's enclosed in a function! It's easy to see believe callbacks == arrow functions and methods should be regular functions, but it's also important to step back and think, what would Jack Skellington ask? 
