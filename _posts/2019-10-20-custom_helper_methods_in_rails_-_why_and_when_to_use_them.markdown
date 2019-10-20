---
layout: post
title:      "Custom Helper methods in Rails - why and when to use them"
date:       2019-10-20 14:51:48 -0400
permalink:  custom_helper_methods_in_rails_-_why_and_when_to_use_them
---

One of the reasons I wanted to write a bolg about helper methods in Rails is becouse while I was working on my Rails application, often times I would get confused about which methods should be created in the model, and which should be created as helper methods. 
So I wanted to share my thoughts about this issue and perhaps help someone else who is confused. 

**A refresher on MVC in Rails**

The MVC pattern is designed to implement the concept of separation of concerns in a web application.
MVC stands for Model, View and Controller, and in a Rails application we can find the models, views and controllers folders inside the app directory. 

* *Model* -  handles the data in the app. It is responsible for things like retrieving, sorting, deleting and updating data.

* *Controller*  - is responsible for the decision making and logic of the application. It pulls relevant data from ActiveRecord and performs functions on the data like saving it. 

* *View* - the web page rendered to the client. Where the client using the app can see and interact with it in the browser.


**Rails Helpers**

> Helpers are methods that are available to your views and encapsulate a common bit of code. --learn.co
 
Basically the helpers help you implement logic in your views. And why do we need help in getting logic into our views? That's right! Because of the separation of concerns principle! Views are meant to just render a web page to the user, they shouldn't handle any complex logic. 
Rails has a lot of very helpful built-in helper methods that you probably encountered, like `form_with`, `link_to` and `text_field`. 

Rails is really great in enabling you to create your own helper methods. Helpers are organized by controllers, for each controller there is a file in which you can write your helper methods. You can find these files inside the helpers folder.  Though the helper files are organized by controller, they are accessible for any view, so that really helps in keeping your code DRY. 

Great, so now that we understand what helpers are for lets look at some examples from my code and see if a method should be created in a model, or as a helper method: 

```
def self.price_asc
	self.order(:price)
end
    
def self.price_desc
	self.order(price: :desc)
end
``` 

The methods above are responsible for presenting products in either an ascending order, or a descending order.  The `order` method is a query method and an ActiveRecord class, hence it deals directly with the database. 
So should it be in the model? Yes!

And how about this method: 

```
 def created_time
	self.created_at.strftime("%b %e, %Y at %l:%M %p (UTC)")
end
```
This method refactors the created_at property to a more readable date and time string, using  the `strftime` method. Should this method be in the model? No! 
This method deals with presentation: how it should be rendered, no what should be rendered. 

This method belongs to my `orders` controller, hence it should go to the `order.rb` file inside of the helpers folder:

```
def created_time(order)
	order.created_at.strftime("%b %e, %Y at %l:%M %p (UTC)")
end
```
In my orders show view it will look like this: 

```
<h4>Order Created at <b><%= created_time @order %></b></h4> 
```

That's it, I hope this blog entry helped you to understand helper methods more, and more importantly when to use it. 


