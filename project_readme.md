
1. deploy link
2. "Guided Tour" path the reviewer should follow when reviewing the app in the browser.
  - highlight the best (and most challenging) parts of your app.
  - detail exactly the steps that the reviewer should take in order to review your app. They will certainly poke around in other ways but this will save them from having to think about what to review first.
3. explicit instructions for how to use the app, if different from the Guided Tour or more complex.
4. "Technical Highlights" section
  - briefly how the application is constructed (remember that they will receive submissions from people with all sorts of backgrounds) and some bullet points with the key technical parts you think will highlight your skills well (e.g. an algorithm you used or a way you made it faster or a trick of the architecture).
  - Don't be shy about highlighting the things you did to make this awesome -- remember that reviewers will otherwise probably miss these things.
5. how to download and run the repo on their machine. Test these instructions yourself.



##How to download and run on your machine
- Clone this repository and run bundle install to install the required gems
- Set up and seed the database by running rake db:migrate && rake db:seed in your console
- Run rspec to check for errors
- Start up your rails server and play with the app on localhost:3000 in your browser
- Enjoy!



#[Codelegy](www.codelegy.xyz)
Web app to connect people looking to pair-program
- Created, with a team of 6 developers, a pair-programming network site using Agile Development to allow continuous integration of new features.
- AngularJS app using Ruby on Rails as an API featuring customized mailboxer gem for email subscription, Omniauth for external website logins, and Devise.

##Technical Highlights
-developed a networking web app to find people to pair program and learn with.  This is a Ruby on Rails application with angularJS on the Front End, Continuous Integration with TravisCI, OmniAuth, and email subscription.
-worked on a team of 6 people
-personally worked on emails and subscriptions using mailboxer gem


#[Danebook](www.github.com/aliceFung/danebook)
A Facebook clone: a Ruby on Rails web app deployed on Heroku with images hosted on Amazon S3. This features sign up, posting, liking, commenting, friending, emails, and photo uploading

-Completed a basic Facebook clone where users can sign up, post, comment, like things, friend users, and upload photos.
-Ruby on Rails app featuring mailers, delayed job queues, AWS S3 integration, AJAX requests, and a full test framework.

##Guided Tour

##Technical Highlights
- Completed a basic Facebook clone where users can sign up, post, comment, like things, friend users, and upload photos.
- Ruby on Rails app featuring mailers, delayed job queues, AWS S3 integration, AJAX requests, and a full test framework.

###Database
how associations set up
###Testing
####Unit Tests
if error cases allowed, works as expected
####Behavioral Tests
how user will use it
###Back-end
any proud methods
###any thing I'm proud of



#Game Center
[try it here]()

##Tetris
set difficulty, play, how long can you last
algorithm for rotation, reusable code, remove unnecessary computation

##Snake
set difficulty, play and don't hit the walls or yourself
grid > animate for movement

##Memory
set difficulty, play and try not to cheat




#[Djello](github.com/aliceFung/project_djello)
Trello Clone: project management app

-Built a lite Trello Clone where users can create, edit and delete boards, lists, cards, and card members.
-Uses a Ruby on Rails API to create an AngularJS Single Page App using services, ui-router, and modals.

##Guided Tour
Visit Djello
Sign in with :
Create, Edit, or Delete Boards, Lists, Cards
Complete a Card

##Technical Highlights
###Database
how associations set up!!
###Testing
####Unit Tests
if error cases allowed, works as expected

###front-end: Angular
Restangular,
ui-router,
Devise,
angularModalService
###Back-end
rails API, n+1 query avoided
any proud methods, methods to move info from list to list
###Front-end
reusable code


#[Qubits Learning Center](qubitslc.com)
in person 1 on 1 academic and SAT tutoring in Seattle, WA

###tumblr post
-inline everything vs. security
-handroll vs premade: bug fixes, etc. ie: potato battery lightbulb

responsive static website for client
## Technical Highlights
-minimizing latency: img reduction/compression, minifying/uglifying, reducing files required
-search discovery: SEO: site submission, site map: search web crawling, accessibility
-multiple iterations


#[Catch A Truck](www.github.com/aliceFung/catch_a_truck)
San Francisco foodtruck locator
- Developed an AngularJS Single Page App using Ruby on Rails as an API to preprocess data; features Google Maps.
##Guided Tour
##Technical Highlights


#[Concerts Near You](github.com/aliceFung/concerts_near_you)
A Ruby on Rails app to locate nearby concerts
- Collaborated with 2 others using git merge workflow to deploy app within 2 days for a hackathon.
- Integrated Geocoder gem, different event APIs, and Devise for user signup via Facebook and location default setting using user IP address to locate upcoming events near user location.












_______________________________________________________

#####tl;dr

I graduated from Johns Hopkins with a degree in Neuroscience. While I was working at a medical office










-----------------------------------------------------














#### Geting Started
*  Clone and run `bundle install` to install the required gems
*  Run `rake db:migrate && rake db:seed` to get the database initialized
*  Run `rspec` to make sure everything is working
*  Fire up your `rails server` and head to localhost:3000 to check it out!

This is [Alok's](https://github.com/alokpradhan/food_truck_app) and [Joseph's](https://github.com/joseph-lozano/food_truck_app) try at [Uber Coding Challenge #4](https://github.com/uber/coding-challenge-tools/blob/master/coding_challenge.md#food-trucks).  This is a full stack application, making use of a Ruby on Rails API to serve data to an Angular front-end. Check it out [HERE](http://stormy-wave-6805.herokuapp.com/)

#### Walkthrough
##### Database
The database is seeded from [data.sfgov.org](http://data.sfgov.org/resource/rqzj-sfat.json). It is then split into 3 tables, a food_trucks table, which stores information on each facilities' name, type, and what food items they have. The locations table stores location information, including latitude and longitude, address, and the location description.

Because food_trucks and locations have a many-to-many relationship, they are joined by an operations table, which also keeps track of operating hours for each truck at each location.

##### Testing
###### Controller Testing
Because our app is primarily an api to serve the front end, looking at the controller tests gives a great opportunity took look at the capabilities of the app.  Our API can receive location data in three formats, a string, such as `123 Fake Street, San Francisco, CA`, an JSON array or latitude and longitude coordinates, or as an IP address. In each of these cases, the controller successfully returns a JSON response object to the front-end, and limits the responses to 26.

Otherwise, if the location given is outside of San Francisco, the returned JSON object has a length of zero. That is, there are no nearby food trucks.
###### Model Testing
Our FoodTruck model is contains the search methods, called `FoodTruck.data()`, and so our model tests for data check that this method works properly. In addition, it also checks that FoodTruck has both the Location, and Operation associations.

##### Back-end
Our `FoodTruck.data()` method takes one argument, that argument can be either an address string, a stringified array, or a stringified IP address. Our if/else block parse through each possibility, and converts the address into an Array, and passes it onto the next method. `trucks_near_location()` Takes the array from the previous method, and a fixed radius, and returns an array of all trucks within that radius. If there are less than 26 trucks found, it will expand the radius, and search again until exactly 26 are found; `nearby_locations` is a helper function.

##### Front-end
Our Front-end is built on Angular. We used Angular to take use of services, small modules of code. We have 3 services. A userPosition service, which grabs location data from the browswer, a map service, which renders the map, and contains the functions for add markers to the map, and a data service, which talks to the Rails API.

All of these serve a slim angular controller which simply handles ng-model objects and functions from the html page.

#### Guided Tour
Step 1. Visit [SF Food Truck Locator](http://stormy-wave-6805.herokuapp.com/)
Step 2. a. Click on the 'Search Near Me' button to find a list of food options near you, or...
Step 2. b. Search for food options at any street address in San Francisco. Enter details and click on the 'Search by Address' button
Step 3. Scroll down to see a table populated with the locations, times, and menu details of trucks and stalls
Step 4. Enjoy a great meal!

