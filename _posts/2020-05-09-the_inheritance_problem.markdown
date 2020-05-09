---
layout: post
title:      "The Inheritance Problem"
date:       2020-05-09 23:03:21 +0000
permalink:  the_inheritance_problem
---


![](https://66.media.tumblr.com/8bc045d33bb45df82a0be40af6e118df/tumblr_nhoynd23fJ1rw4rkuo2_500.gifv) 


Well not so much a problem. Just the trickery that comes with JavaScript inheritance. I came from a Ruby background, class inheritance was pretty standard. And when I started to learn JS, we were using the fancy ES6 syntax which does create classes in a fairly simple and dare I say pretty way. 

```
class Cat {
  constructor(name) {
	  this.name = name; 
	}
}
```

Simple! Readable! And creating a child class (inheritor) of said class would look something like this. 

```
class Cat {
  constructor(name) {
	  this.name = name; 
	 }
	
	meow() {
	 console.log("meow"); 
	}
	
	purr() {
	  console.log("*purr*");
	}
}

class Munchkin extends Cat {
  constructor(name) {
	  super(name);
		this.leg_length = "short";
	}
}
```

Besides the `super` keyword, which explicitly calling the parent constructor, simply adding extends gives Munchkin cats all the abilities that Cats have, they can purr or meow. However, they do have tiny legs. So far, so good. 

But working in JS you do start to hear about "prototypes", and how JS uses "prototypal inheritance". Strange, since this looks fairly similiar to other languages that use `class`. Well, this class inheritance structure is built on top of JavaScript's prototypal inheritance system, it's all just smoke and mirrors! JS has a prototype chain, and that's how all inheritance works. 

Any class you create is really creating an object *with* a prototype object, and a prototype can trace itself back to the OG -- the Object.prototype. And since all prototypes can reference the constructor that called it, we can model inheritance that way. That's why there's a *prototype chain*. So, implementing the above examples with cats and Munchkins. 

```
lily = new Cat("lily"); 
pippin = new Munchkin("pippin"); 

pippin.meow(); 
```

Invoking meow works with a Munchkin instance because even though JS can't find the property in Munchkin, it can follow the chain back to Cat, which does have a function that defines "meow" .  

The syntatic sugar that ES6 introduced with `class` is interesting. The inheritance system didn't change, prototypes are all there under the hood. And now it's more in line with OOP, the classic, widely taught programming pattern in this day and age. Which is why it's still sort of jarring to see prototype references and tutorials when talking about JS inheritance. It's almost entirely possible to learn how to write JS using classes and not referencing the prototype at all. In fact prototypes are starting to feel more like a gotcha question in an interview rather than a key part of implementing objects in your code. I was certainly confused by it until I did a bit more digging. 

Technology marches on, and I'm sure this problem will soon disappear. 



![](https://milk.imgix.net/2014/12/3322-giphy-2.gif?auto=format&fit=scale&h=328&ixlib=php-1.1.0&q=95&w=490&wpsize=article-aside&s=de91e0c94727ec2341bd55f8fc47923c)
