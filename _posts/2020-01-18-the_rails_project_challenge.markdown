---
layout: post
title:      "The Rails Project Challenge"
date:       2020-01-19 04:11:20 +0000
permalink:  the_rails_project_challenge
---


I took a rather esoteric and strange route for this project. I thought it would be fun to make a demon summoning app. While the coding of it was straightforward, figuring out the ActiveRecord associations was surprisingly difficult, and is what caused the most problems. 

I knew I needed a Demon model and a User model. The users would summon demons -- therefore there should be a summon model as well. But what does the summon model require? Presumably some ingredients people would use in summoning. I originally thought of this as just a simple array that you can update in the database. But as my instructor pointed out, it might be best as another model. With that in mind -- I created a Sacrifice model that belongs to both a demon and a summon. 

A user has many demons through summonings. 
A demon has many users through summonings as well. 
A summons has a demon and a user, as well as a sacrifice. 
A demon can have many sacrifices. 
A sacrifice has many summons but only one demon. 

Looking at it this way I was able to see which routes worked bested as nested routes. A summons should be called from a user who can choose what demon they want or a specific demon someone found on the index page. However, getting to the point where I understood the relationships best took a bit of back and forth, and some rollbacking of migrations as well. While I wish I could've had a clearer vision so that I didn't need to do so much revision with the database, I'm not sure if it's always going to be avoidable.

In any case -- summonings ahead! 
