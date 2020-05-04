---
layout: post
title:      "Git Gud:  Keeping Your Git-Sanity"
date:       2020-05-04 21:21:44 +0000
permalink:  git_gud_keeping_your_git-sanity
---


![](https://i.kym-cdn.com/photos/images/original/000/693/282/c81.gif)

Sorry not sorry for the gif. 

As a developer, I sometimes go for long periods of time where the only git repos I need to use are my own. I don't have to worry about messy merges. I'm not concerned if no one understands the weird phrasing of my commits. But then I'm on a team again, and well...it's time to *git gud.* 

Alright folks -- git is a version control system. If you're like me and have a father who used to code with punch cards, you'll hear things like "back in my day we didn't have any fancy versioning software, if there was a bug you had to start all over! And then you died!" He might not have said that verbatim, I certainly wasn't listening. 

It's a distributed system! So not a single person will own an entire codebase on their own machine. And as long as you don't mess it up (which will happen, sorry that's just an inevitability even with cheatsheets), you don't ever have to worry about accidentally losing work, or ruining a project forever with terrible code. 

So working alone, `git add` and `git commit` are fairly unbequitious. You're adding your changes, and telling git -- look, these are new things! It will take a snapshot of this data to add to it's internal storage (which from my research is a nice trie structure) and then you can `git push` your code to a remote repo that other people can then `git pull` from and get all your lovely changes! 

This `git pull` is a little unfamiliar for those unused to working in teams. However, given that you push code out, it's fairly easy to grasp that to get the changes other people make -- one would need to *pull*. But the thing that always, always, always, escaped me was `git fetch`. You can't pull changes that haven't been fetched. 

But the big thing about having git, is the branching. Some people have tried to convince me that branching is the most important part of git. And is something that you should be doing even as a solo programmer. When branching was first explained to me, I couldn't visualize it or understand it very well. 

Branches create a copy of the code, for someone to add a feature or experiment with. Then they can come back around and `merge` their changes with the 'original' branch or another branch. While not all branches are used and are instead dropped, the most important thing when coding on your little branch is that the goal is to come back to the original. Which is why making branches of branches seems like such a dangerous and confusing idea. (But also all too easy to do when you think you're in the original...) 

This is just a quick overview. And more to keep in mind the important parts of using git in a team. However this can all be applied to solo programming. Always keep in mind features in your project roadmap and maybe consider splitting them out in their own branch? Then you won't be taken by surprise when you get back on a team! 
