---
layout: post
title:      " CLI Project- Yoga-Pose-Finder"
date:       2018-09-20 21:04:52 +0000
permalink:  cli_project-_yoga-pose-finder
---


For my CLI project I wanted to create an app that means something to me and that I would use. 
As a yoga teacher and  practitioner, I know that practicing yoga can help in many areas in life,
it certainly  helped me a lot, and I wanted to share this using my app.
Searching aroung I found  a site called 'yogajournal.com' in which there's a  'yoga by benefits' option that containes an index page of 25 different 'yoga for- ' categories, like, 'yoga for stress', 'yoga for weight loss' etc.
Each category is also an index page of different poses, and a click on each pose opens up a page with information about that pose. 
After recieving a green light on the site and the idea I started my project!

So, starting is usually the hardest part, and it definitely was for me..
After watching (almost) all the videos related to the project,
I found that what helped me with starting the process was to think about how I want my app to look like and act like once it's done, describing what will happen with each step. 
For example- first, the user should be greeted, presented with the list of 25 'yoga for' categories and asked to choose a category. Then, be presented with the list of the poses in each category and asked to choose a pose. Once the user chooses a pose he should get information about that pose. 

To do so I created 4 classes: Category, Pose, Cli, and Scraper. 
And now, moving to the really hard part.. writing the actual code!
After sitting for hours on my code, trying different things, I discovered that the best way to approach this task is to write it down in a psuedo-code manner, describing what the methods in each class should do. 
For example: for Category and Pose classes-
1. It should be initialized with a name and URL. 
2. Each instance should recieve attributes.
3. Self.ceate from collection(?)

Scraper class- 
1. Should scrape the categories names and URLs from the categories page.
2. Should scrape the poses names and URLs from the poses' index page.
3. Sould scrape from the pose profile page information, such as: sanskrit name, description, benefits, instructions...

I commented these psuedo-codes at the top of each class file, which helped me to stay focused on the task.
I started working on the Scraper class and scraped the name and URL of the different categories so I could initialize the instances of the Category class. Then scraped the poses index page for each category, and added the poses to it's category. Then it was time to switch to the Pose class and using the name and URL I've scraped from the poses' index page, I created an initialize method that creates pose instances.
During this time I also worked on the Cli class, which acted as my anchor becouse it helped me visualize how the app should look like and be used by the user, and helped me to understand what was the next step in each stage. 
Of course it still got  messy and confusing and it took time and a lot of playing around with the code to understand it better and get it working.

My biggest challenge in the project ended up being scraping the pose profile page and getting the information I needed. 
Inspecting it, it turned out that the page was not very well structured.
Almost all the information was on the same node level, in paragraphs. I wanted to get more information, like pose level and the steps describing how to do the pose, but after trying different methods like Regex, split and join,  I managed to get the sanskrit name, a short description and the benefits. 
The next challange was to discover that even then, some pages were structiored a bit differently, and some poses did not have a sanskrit name, or benefits. So with the help of a few 1:1 sessions, I managed to overcome these bumps and  the program could handle a situation where there is no sanskrit name, or benefits. 
My advice to you is to first check if the site is good for scraping and structured well!! 
I know it's hard understanding what to look for when you just starting on your project, but try and look for nodes, see that the information you wish to scrape is inside a node that is easy to access and differentiate from other nodes. All in all it was a good learning experience and at least now I know what to look for in scraping.. 
So after having the basic structure of the classes and the app was running the way I wanted, I started refactoring the code and make it cleaner and more DRY. 

Over all I had a great time working on my project, it's the first time I'm building an app on my own. I like my yoga-pose-finder app and I'm pretty proud of it :)






