---
layout: post
title:      "My CLI Project Process"
date:       2018-07-02 19:13:05 -0400
permalink:  my_cli_project_process
---


In this post I will I will both outline the process of how I created the [edm_festival_finder ](https://github.com/gitluky/edm_festival_finder)gem.

### **Gem setup with Bundler**

   I never created a gem in my life, so the the thought of having to create and publish a gem was a bit daunting at first. After watching Avi's video and doing some google searches, it turned out to be a simple process after all:

1) run the command to create the framework for your gem: 
	bundle gem <gem name>
2) update the gemspec file details and add dependencies
3) create an environment file that requires all your lib files and require it in your bin file
4) when the gem is completed and ready for publishing, enter the following commands:
	gem build <gem name>.gemspec
	gem push <gem file built from last command>
5) to remove a gem version from rubygems.org, enter command
	gem yank <gem name (minus version number)> -v <version name>
	
*Note: the gem will be taken off of rubygems, but the same version number cannot be resubmitted again*

### **Building edm_festival_finder**

**    The first thing I started to code was the CLI class, I wanted to paint a picture of how the user would interact with the application. I broke down each step the user would take to eventually get to the details of each festival and thought of the methods I would need to get there. Here was my thought process and how I figured what I needed to build:**
		
**1) after running the application, the user will land on the title screen and be prompted to press enter**
	    a) I will need a call method in the CLI class to start the application
	
**2) a list of countries will be displayed**
	    a) I will need a method in my Scraper class to scrape the countries from the website
	    b) I will need a method in my CLI class to display the countries to the user
	
**3) the user will select the country**
	    a) I will need to validate that user input matches the countries scraped
	
**4) a list of festivals will be displayed**
	    a) I will need a method in my Scraper class that scrapes the festivals found
	    b) I will need a method in my Festivals class to create festivals from the scraped data 	and store it into a class                           variable
	    c) I will need a method in my CLI class that displays the Festivals from the Festivals 	class variable
	
**5) user selects the festival**
	    a) I will need to validate user input for festival selection
	
**6) the festival details will be displayed**
	    a) I will need a method in the Scraper class that scrapes the details page of each 	festival
	    b) I will need a method in the Festivals class that adds these details to existing festivals
	    c) I will need a method in the CLI class to display the festival details
	
**7) anywhere in between, the user should be able to go back or exit the application.**
      a) I will need a method that checks for 'back' or 'exit' everytime there is user input

### **Saved by Xpath**
   The trickiest part for me was trying to pinpoint the correct selectors to use to scrape the data that I wanted. Still, when looking back at my code I have a feeling that I may be able to do a better job, but for now, it works and that's good enough for me. I spent hours trying to select two different elements with the same classes but wasn't able to work it out until I learned how to use the Xpath method. Here's a tutorial that I found that helped me.
http://thaiwood.io/screen-scraping-with-a-saw-a-nokogiri-tutorial-with-examples/

### **Biggest Lesson Learned**
   At first, the gem I was going to build was an Escape Room Finder that would scrape Yelp for the top Escape Rooms based on the location the user provided. The big mistake I made was that I assumed I would be able to scrape from all websites. I built most of the initial project out without even testing whether I was able to scrape Yelp, and when I finally decided to run the application to see whether any results would be returned, I received the 503 - Service Unavailable error. I did a few google searches and found out that sometimes this error message would appear when a website is undergoing maintenance and it may come back up after a few hours. After waiting a few hours I tried again, and still, I was getting the same error message. A few more google searches later and after reading Yelp's  Terms of Service Agreement, I realized that Yelp prohibits scraping of their website. Bye bye, Escape Room Finder. Lesson learned: always do small tests to check first.
    This lesson extends even further than the hiccup with Yelp that I ran into. When writing code, I originally utilized the process I typically used to write essays and papers - loosely drafting everything out completely first, then going back to delete, add and clean up the writing. But the process to writing code should be different, it makes more sense to me now to break the application into small chunks of functioning parts, and continuosly test while writing each chunk of code before putting it together to have the complete application.
