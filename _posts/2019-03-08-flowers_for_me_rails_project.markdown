---
layout: post
title:      "Flowers for Me Rails Project"
date:       2019-03-08 22:14:45 +0000
permalink:  flowers_for_me_rails_project
---


For my ruby on rails project I decided to create an application which allows a user to put an order for flower arrangements. I wanted to write an app that I would relate to and enjoy writing, and as a florist, I chose to create an noline flower delivery service app. 

So writing this app was a journey for me. I started the project after a short brake due to a vacation and moving to a new state, so it took me a while to return to the loop and remember the material from the rails section. It was challenging and at times very frustrating. Things didn't work, I didn't understand why they don't work, you know the drill.. 

But things shifted after a week or so, when I just started making it look and work as if I will actaully use it. The thing that got me invested and enjoy building my app was adding photos. As I was browsing through online flower sites to get some ideas, I realized that a flower app without photos of flowers doesn't make any sense. Then I looked through my own photos of arrangements I made when I was working in a flower shop, and that got me excited and motivated to learn more and apply new features, like installing the Carriewave gem for uploading photos.
Making it work was also challenging, but I succeeded, and that gave me more motivation to try new things, like using the bootstrap gem. 

Going back and forth through the lessons and  watching the lectures really helped to understand the whole structure of a rails app better. Slowly things atarted to click more. terms I've learned during the last few months and heard over and over again suddently really sunk in. Let me tell you, the profession we chose is not easy! It takes time to understand these concepts. it takes time and effort to learn new things, but once something works, once you understand one more thing you didn't before, it feels great! 

So a little about my app: 
I used a User, Order and Arrangement models. 
The user has a name, email, address, password and admin attributes.
The arrangement has a title, description, height, price and image attributes. 
The order is acting as the join table and has a user_id, arrangement_id, quantity and a deliver_day attributes. 
So the user has many arrangements through the orders table, and an arrangement has many users through the orders table. the order belongs to a user and an arrangement. 

Only a logged in user can watch the arrangement collection and make a new order, and only the admin can add new arrangements or edit and delete them. 

I used the Bcrypt gem and added the has_secure_password to the user model.  This anabled me to authenticate users in the login precess. 

For an additional  authentication source I used the Omniauth gem and Github-Omniauth. 
Watching the Omniauth lecture in Learn was very helpful for this. If you follow the instructions of the set up it should work with no issues. The only thing that gave me some problems is a security error I got when trying to authenticate through github. I found that clearing the history of the page fixed it. 

Overall I tried to keep it DRY, and let methods in the models and helpers take care of the logic part of the code, and leave the views and controllers as thin as possible. 

In this project it was the first time I used the 'raise .inspect' debugging,  and I found it very helpful. It really helped me understand why things are not working and keep me focused on fixing the problem. 

Another tool that really helped and I am turning to it more and more is good old Google! 
Before this project I usually was trying to go back to the curriculum when encountered an issue in a project, and it is helpful, but this time I used google more, and I learned a lot. 

For conclusion, my advice is, don't give up, don't be intimidated from all the forums and blogs out there, use them! you will slowly start to understand more and more, be patient. And find something that gets you axcited when creating an app. It will make it real and fun and give you motivation. 






 



