---
layout: post
title:      "YawdSale - My CRUD, MVC, Sinatra app baby "
date:       2019-03-06 20:35:35 -0500
permalink:  yawdsale_-_my_crud_mvc_sinatra_app_baby
---

I’ve completed birthing my YawdSale web app for my Flatiron School Sinatra Final Project and it has been a long and trying process – filled with moments of complete frustration and feeling like a total noob balanced by rewarding moments of overcoming challenges that hit me like a wall. Let’s face it, nothing is ever really ‘done’, but I feel like I’ve gotten it to the point where I can say that I am happy with how it is currently is considering all that I’ve learned from this program so far. Secondly, it meets the requirements for the project, which was to build an app with the Models, Views, Controller framework and CRUD routes with Sinatra.
YawdSale is a simple application – users can sign up for an account, and after signing up, they can post their own YawdSale (yard sales, with a southern twang), see nearby YawdSales according to the home address in their profile, and search for Yawdsales by location data. Users can edit their profile and the information for the YawdSales that they have created, including adding and removing photos to the YawdSale. The app uses the Ruby Geocoder gem ([](http://www.rubygeocoder.com/)) and the Google Maps API([](https://cloud.google.com/maps-platform/maps/)) to geocode the addresses for the User and Yawdsale models.
Rough Process:
When I was working on this project, I was all over the place – there were days where I obsessed over html/css even though there weren’t any requirements on aesthetics; I was unsure to whether I was going include the functionality to add photos, I waited until the end to figure this out. I generally tried to follow this process which I’ve broken down into 4 stages:
# Stage 1: Set up

* Brainstorm what models and application controllers are needed, what pages are needed by the user to navigate through the site
* Set up the file/folder structure – creating all MVC folder
* Creating environment.rb, config.ru,and Rakefile
* Define the classes for the models and establish relationships
* Create the migration files and seeds.rb
* Run rake db:migrate and rake db:seed, play around with the models, verify relationships

# Stage 2: Happy Path
* Create the controllers needed and add them to config.ru
* Build out each route and simple show views to display object data
* Create the ‘new’ routes and views with forms
* Create the ‘edit’ routes and views with forms (most of which can be copied and pasted from ‘new’)
* Identify and create the remaining routes and views, in my case, I wanted to have a search route

# Stage 3: Validations and not-so-happy-paths
* Add validations, conditions that need to met in order to enjoy the happy path, for example, verifying that the user is logged in, verifying whether the correct user is logged in, validating user input, etc. before letting them perform and of the create, read, update and delete functions.
* Make sure you are redirecting the user to the appropriate pages and prompting them with the correct error messages.

# Stage 4: Facelift
* Update the views and make the app look more aesthetically pleasing than a text document.

# Some things I’ve learned:
1)	I spent days trying to set up rack-flash. At one point I decided just to remove it from the app and not deal with it. I had set it up in a previous lab and it had worked perfectly fine, but for the life of me I couldn’t get it working on this project. I came back to it with determination and after entering many permutations with keywords ‘rack-flash across controllers not displaying message Sinatra’ into google, I landed on a comment on some random thread that mentioned that rack-flash required that a :session_secret be set when running your app with shotgun ([](https://groups.google.com/forum/#!topic/sinatrarb/pUFSoyQXyQs)).
Now it’s simple as just adding gem ‘rack-flash3’ into the file and setting up your ApplicationController like so:


```
require 'rack-flash'

class ApplicationController < Sinatra::Base

  configure do
    set :public_folder, 'public'
    set :views, 'app/views'
    enable :sessions
    set :session_secret, "somethingrandom"
    use Rack::Flash
  end


end
```


2)	 I never used Geocoder so I was bound to run into some issues, but it wasn’t too bad. Most of the information sources that I had seen mentioned that Geocoder by default uses google to lookup addresses, this wasn’t the case for me, I had to manually configure it to use google and to take my API key. For more information on obtaining a Google Maps API key, visit [](https://cloud.google.com/maps-platform/maps/). DO NOT HARDCODE YOUR API KEY. I placed my key in a text file one directory up from my project directory and added this line to my environment file:
`Geocoder.configure(:lookup => :google, :api_key => "#{File.read('./../apikey.txt')}")`

Setting up the model to be able to use Geocoder with Sinatra only required four additional lines, and a method to combine address elements into one single string if you had them separated. 
Example:
```
class User < ActiveRecord::Base
  extend Geocoder::Model::ActiveRecord       #1

  has_many :yawdsales
  has_many :photos, through: :yawdsales

  has_secure_password

  geocoded_by :address   #2
  reverse_geocoded_by :latitude, :longitude  #3
  after_validation :geocode  #4

  def address  #needed if parts of address are separated into different columns
    [street_address, city, state, zipcode].compact.join(', ')
  end

end
```

3)	Instead of writing all the html/css from scratch, I decided to go with Bootstrap especially since I didn’t want to write media queries. I found out that on the Bootstrap site, you can quickly copy and paste together a Frankenstein looking site with provided navbars, buttons, cards, etc. Bootstrap comes with plenty of pre-scripted classes that makes it super easy to position elements if you know what they are and where to put them. I didn’t…so it took me some time to figure it out. I also discovered MDBootstrap, which is pretty much Bootstraps sexy cousin. The colors pop a little better in my opinion, but they share the same class names, but some modification has been done to the classes so that in itself created some surprising issues - elements shifted positioning and my buttons stopped working.

4)	I learned out how to implement a file upload feature. I wanted the user to be able to upload up to three photos, and in the back end it would be saved in a yawdsale.id/photos folder. This was the guide I followed: [](https://gist.github.com/runemadsen/3905593)

All in all, although it has taken me far longer than I’d like to admit, I have learned a lot from working on this project and am ready to continue on my path to becoming a professional developer.

