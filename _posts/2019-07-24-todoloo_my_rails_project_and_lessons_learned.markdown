---
layout: post
title:      "ToDoLoo: My Rails Project and Lessons Learned"
date:       2019-07-24 21:08:11 -0400
permalink:  todoloo_my_rails_project_and_lessons_learned
---


For my Rails project, I wanted to create a web app in which people can manage small projects like planning a trip, setting up a weekend barbecue or a small get together. The idea was simple enough —sign up, create a group, invite other users, create tasks, share notes and post announcements. It did take me longer than expected to complete, but I typically take some extra time on these projects to play around – do some trial and error in order to strengthen my understanding of how things work. Could I have worked at a more aggressive pace? Sure, but I’ve also learned to adopt a new kind of attitude in terms of work and life in general through my experience working on this project. There were definitely days that I struggled and became unmotivated, but the most important lesson I learned from this, not even being code related, is to enjoy the process, no matter what it is you do, focus on what you are doing at the moment and pay less attention to the results, the results will be the side effect or the hard work you are putting in. 

#My Process:

The first thing I did was create a notes document and listed all the classes/models I needed along with all the relationships between them. It was a simple copy and paste from this document into the correct files, and all my models and database tables were up and running. After that, I thought it would be a good idea to tackle each functionality one-by-one based on how a user would use it, to build out a Minimum Viable Product first and add functionality to it.  

The steps for each were roughly:

1)	Generate the resource

2)	Set up the routes

3)	Create the view files

4)	Build the controller actions along with their views

5)	Refactor and move logic over to the models and helpers, and cleaned up the views using partials

I repeated these steps for each functionality: sign-up, authentication (both internal and Facebook OAUTH), and for each controller action for groups, invitations, announcements, tasks, and notes. In terms of validations and error handling, I had a separate step at the end to add them in, but in most part I sprinkled them in as I built the app.
I didn’t take the TDD approach for this project, I wasn’t confident with my ability of writing test cases with Rspec and Capybara at all, I just wanted to get started on the project and think about it afterward. In the end, I was able to squeeze in some practice writing a decent amount of feature tests for both happy and negative paths and I feel quite capable now. 

#My Takeaways

Next time, I will use the TDD approach as it helps with the planning; there were times that I was lost because I didn’t fully think out how I wanted to certain features to be and writing tests is a good way to spell it out. I also got derailed a few times after introducing bugs as I added more code, and having a test suite to run each time would have helped identify problems sooner.

