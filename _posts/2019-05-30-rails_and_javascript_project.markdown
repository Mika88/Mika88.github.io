---
layout: post
title:      "Rails and JavaScript project"
date:       2019-05-30 19:02:46 -0400
permalink:  rails_and_javascript_project
---


For my JS project I’ve used my ‘flowers-for-me-app’ I’ve built for the Rails project.

The first challange was to decide which index and show pages to render, in order to reveal the ‘has-many’ relationship and submitting a form via JS while accomplishing it in a fluid and sensible way. After a few trial and error attampts I’ve found the right way so I could meet all requirements:

* Rendering the index page - I’ve hijacked the ‘arrangements’ button in the navbar to render a list of all arrangements to the page.

* Rendering the show page - each arrangement title on the list served as a link, by clicking on the link the show page for that arrangement was rendered.

* Reveal a ‘has-many’ relationship - each arrangement has many orders, so I’ve creaed a link on the arrangement’s show page that once clicked, a list of the arrangements’ orders is rendered.

* Submit a form- on the arrangement show page I’ve created a link to a new order form, redirecting to the rails route for a new form. The submission of that form was done through a jQuery post request, and the data I got back in the callback function was used to create a new order and rendering it to the page.

For each page the work flow was quite similar, let’s take the index page of arrangements as an example:

Creatig a click event:

```
$('#all_arrangements').on('click', (e) => {
	e.preventDefault()
	history.pushState(null, null, "arrangements")
	getArrangements()
})
	```

Sending a jQuery get request to get a json object with the data:

```
const getArrangements = () => { 
  $(‘#container’).html(‘’) 
  $.get(“/arrangements.json”, function(arrangements){
     })
 })
} 
```

Building a new object using a constructor syntax:

```
function Arrangement(arrangement) {
		this.id = arrangement.id
		this.description = arrangement.description
		this.height = arrangement.height
		this.title = arrangement.title
		this.imageUrl = arrangement.image.image.url
		this.price = arrangement.price
		this.orders = arrangement.orders
		this.users = arrangement.users
    }
```

Creating a prototype function to render the html format to the page:

```
Arrangement.prototype.arrangementFormat = function() {
	 let arrangementInfo = `
			 <h3>${this.title}</h3>
			 <h4>Description</h4>
			 <p>${this.description}</p>
			 <h4>Height: ${this.height}</h4>
			 <h4>Price: $${this.price}</h4>
			 <p><img src=${this.imageUrl} height="300" width="300"></p>
			 <a class="orders_list" data-id="${this.id}" href="/arrangements/${this.id}/orders">Orders History</a>
			 <p><a class="make_order_link" href="/arrangements/${this.id}/orders/new">Order Arrangement</a></p>
			 <button data-id="${this.id}" class="previous-arrangement">Previous</button>
			 <button data-id="${this.id}" class="next-arrangement">Next</button>
	 `
	 return arrangementInfo
 }
 ```
 
Using the data retured from the get request to create a new object instance using the constructor, and call the prototype method on that new object:

```
 const getArrangements = () => {
		 $('#container').html('')
		 $.get("/arrangements.json", function(arrangements){
				 arrangements.forEach(arrangement => {
						 let newArrangement = new Arrangement(arrangement)
						 let arrangementList = newArrangement.arrangementIndex() 
						 $('#container').append(arrangementList)
				 })
		 })
 }
	```
	
I must admit that switching between two languages in one project is quite confusing at first, espacially when being so used to Ruby for the majority of the curriculum.

However, after playing around with it for a while it gets more familiar and intuitive.
