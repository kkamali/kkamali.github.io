---
layout: post
title:      "Sinatra CMS Project"
date:       2019-12-06 17:55:51 +0000
permalink:  sinatra_cms_project
---

To continue with my video game theme that I had from my CLI project, I decided for my Sinatra project to create a video game CMS. It would be a simple system, with users who would have many video games. Users didn't need much more than an email, username and password. The username and password would be used for logging in. With the way I work, it was important for me to start with the migrations. 

My users: 
```
    create_table :users do |t|
      t.string :email
      t.string :username
      t.string :password_digest
    end
```

The video games that belong to them required: 
```
    create_table :games do |t|
      t.string :title
      t.string :developers
      t.string :genre
			t.integer :user_id
    end
```

(I made a silly mistake while I was first working on my project -- I forgot the user_id in video games and spent a bit of time curious as to why there wasn't a proper association!) 

From there I created all the erb files for functionality. Having them in place as a reminder, I could then create user and video game controllers. It was an interesting back and forth, adding to the html from what the controllers needed, but also adding more routes due to the needs of the views. 

Once all the routes were working, and there was appropriate views for each, I added checks for users being logged in to make changes or add new games. This came from the helper methods in the main application controller: 
```
  helpers do
    def logged_in?
      !!session[:user_id]
    end

    def current_user
      User.find(session[:user_id])
    end
  end
```

And crucially, only owners of the games could edit or delete the games. Then I also added slugs in the video game models to make the routes more clear. Then to add a bit of my own personalization, I changed the corneal background color CSS! 

Well, I'm less than impressed with the final product (seeing how I interact with amazing web apps everyday) -- I'm proud of how easy the process of deciding how the MVC framework should look, what models I need, how they interact is. 
