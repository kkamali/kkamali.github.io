---
layout: post
title:      "Rails and Javascript -- Demons and Letting Go"
date:       2020-02-16 19:33:16 +0000
permalink:  rails_and_javascript_--_demons_and_letting_go
---


For my rails and Javascript project I was stuck between two former projects that I thought I could improve. After a bit of peer pressure from my friends, and the Valentine's Day spirit -- perhaps re-writing my demon summoning app as a game to woo a demon to you would be a great idea. I was also struck with how quickly my friends gave me my needed assets -- the game was written and the UI was presented to me to implement and well, that's how I was stuck making it. 

I'm used to Unity -- and having a dedicated game object to maniuplate. Since I wanted more of a CRUD application type of project, I did away with that concept. Through a lot of trial and error, that continued throughout the process -- my models and objects took shape. I was surprised by what I thought was going to be useful, turned out not needed. For example, I have a summon -- it's between a user and a demon. Since players and demons could be mixed and matched (and I thought I was going to have a save function for some reason), my initial inklings were to create an 'affection/devotion' type of table. What I realized as I was doing my fetch requests and actually using my API, was that the summons keeping track of how much the demon liked the player was the more logical choice. And saving a game to play later -- when the game barely has any dialogue (hello, it's a demo!) was a silly mechanic as well. 

It's hard for me, when writing code and making applications to always see where things aren't needed. I mean, it's my project from my brain -- and the way that it works to me seems obvious. But the things I code aren't for me, really. It's not fun to create a game that isn't intuitive, it's totally okay to scrap mechanics and things that don't work. The biggest lesson from this project is even with all the planning, all the consideration -- somethings don't make sense in context, and they just don't work. 

And it's okay just to let it go! 
