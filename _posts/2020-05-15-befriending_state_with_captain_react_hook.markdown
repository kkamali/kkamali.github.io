---
layout: post
title:      "Befriending State with Captain (React) Hook"
date:       2020-05-15 20:09:04 +0000
permalink:  befriending_state_with_captain_react_hook
---


Today I asked my friend what to write about. "How about React state management options?" 

![](https://media1.tenor.com/images/01d1d99aa431aa680cc7f8fd805f19bb/tenor.gif?itemid=15229512)

Ugh, really? Sometimes our industry is so boring!

But then I found an [article](https://medium.com/better-programming/react-state-management-in-2020-719d10c816bf)...

"Do we still need state management frameworks?" 

![](https://media1.tenor.com/images/ada0e5dc681821584dbf4561b7269654/tenor.gif?itemid=7666771)

I was immediately enraptured. So it turns out that I am also really boring. The article goes on about React Hooks! A new feature! An answer to my prayers?? 

> However, **hooks are no silver bullet**. Keeping state in a hook does not mean it becomes a singleton, the state is only bound to one component. There are certain uses where we might only want to keep one instance of state (for example, fetching user info only once). This is where a state management framework proves its value.

(Emphasis my own) 

Well, that's less than optimal. And they use one of my least favorite CS jargon words. *Singleton*. It's a word that doesn't stick in my brain meaning what I think it means. The singleton is a pattern (or according to some dramatic critics, an anti-pattern), the one ring to rule them all type of system. It's a sole instantiation of a class. The author is right, hooks aren't singletons -- but it would be better framed as hooks aren't global. The state that we define with a hook is only good for that component. 

In fact, digging deeper into the documentation, the state hooks React has appear to be best for quickly and easily updating state. It also takes away the need for classes and constructors, and no longer do we handle a pesky `this` keyword. (You can see my battle with `this` in [another post)](https://kkamali.github.io/whats_this). 

So to answer the question posed -- yes we still do need state management frameworks. If we got a piece of state and it needs to go multiple places, yes, having a global state managament framework is going to be very helpful indeed. It again goes to show, there's never a one-size fits all solution to any problem in computer science. Just more tools for your toolbox. 


