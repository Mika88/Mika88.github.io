---
layout: post
title:      "You-got-this: my React-Redux project"
date:       2019-08-02 23:40:36 +0000
permalink:  you-got-this_my_react-redux_project
---


So this is it, the last project.. yay!
It's been quite a journey, yes it took me longer than I thought and there were many challenges along the way,
but hey, I'm a web developer, I develop applications and it's so cool!

I guess I'm excited because in this project we had a freer hand in creating what we want, 
and perhaps it was more fun because I knew more and had a little more experience in coding, so I felt that I'm using my skills in developing an app that I woud actually use.

My react-redux app is called  you-got-this and it's a goal tracker application. 
It has three container components that handle the connection to the redux store: 
GoalsContainer, StepsContainer and EventsContainer. 
Each contanier component is a parent to presentational components and class components with a state, if they contain a form.
The StepsContanier is a daughter of the Goal component and the EventsContainer is a daughter of the Step component. 

this is how it works (instructions from the home page):

 => create a goal
=> add your steps
=> for each step create events using the date-time picker
=> add them to your calender
=> once you finish an event or a step check them off 

To get the file system and the components right I went back to the major labs in the React and Redux sections, which helped me in gathering what I need to build it correctly. 

One of my challanges was in using the react router. 
It took me a while to understand how it works and how to write it so the router and  redux library  will work together. 
There where many different approaches out there,  using different npm-s, and after a few tutorials I was starting to grasp the idea and it turned out to be pretty simple.  
My routes are:
* '/' -> home page
* '/goals' -> a list of all the goals
* '/goals/new' -> a new goal form
* '/goal/:id' -> a goal's show page

I had a few more challenges along the way, but using the tools we've been encouraged to use throughout the course, like the almighty google and debugging debugging debugging(!),
I was able to make stuff work and I actually had a lot of fun building this app. 

I especially enjoyed working on the UI, using bootstrap and css. 
After all the logic was there, it was time to make my app look pretty and play around with colors and images, which made it more real and alive. 

The beauty in being a web developer is that you can create apps that you need, that can help you, custom made just for you. like this app for me, a goal tracker that helps me in focusing on finishing the course and get ready for job interviews.

