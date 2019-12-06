# Week 4

[Day 1](#day-1) | [Day 2](#day-2) | [Day 3](#day-3) | [Day 4](#day-4) | [Day 5](#day-5) | [Weekend Challenge](#weekend-challenge) | [Gaps in Knowledge](#gaps-in-knowledge) 

- Build a simple web app with a database  
- Follow an effective debugging process for database applications  
- Explain the basics of how databases work (e.g. tables, SQL, basic relationships)  

---------

## Day 1

### Code review of RPS weekend challenge
- good logic and refactoring; controller was "skinny"
- thorough feauture & unit tests
- forgot to make frequent commits
- can call class attributes directly in views, rather than defining them repetitively in controller

### Pairing (covered many new subjects)
- Practised writing user stories & domain models
- Practised writing/formatting README
- Practised setting up web project from scratch
- Setting up MVC
- Installing PostgreSQL
- Use the psql command to interact with Postgres
- Create tables using SQL
- Use SQL terms like SELECT, FROM, WHERE and * to query a database table  
- Use SQL terms like INSERT, UPDATE and DELETE to create, update and delete database entries
- Attach a database to a web application
  
**What is a database?**

> A database is simply organised part of a filesystem. It's optimised for storing and retrieving data.

**Is Postgres a database?**

> A common database system for modern web development is called PostgreSQL.  
>   
> PostgreSQL is actually a server that runs a database. Therefore, it can be started, stopped, and interacted with through an interface, psql.  
>   
> psql = PostgreSQL's built-in interface  
> pg = PostgreSQL's official Ruby interface

----------

## Day 2

### Goal Setting
- Practise SQL queries; https://sqlzoo.net/wiki/  

### Pairing
- Use database GUIs to interact with databases: Connect TablePlus to your PostgreSQL database management system.  
- Set up a test environment:  
  - You are using the databases in the correct contexts, so that:  
    - When you run tests using rspec, bookmarks are read from the new bookmark_manager_test database.  
    - When you run the application locally, bookmarks are read from the bookmark_manager database.  
  - Write a helper method that truncates (empties) the bookmarks table in the test database before each test run.  
  - Run this helper method automatically right before each RSpec spec, so every test starts with a 'clean' test database.  
  - Add required test bookmarks to the bookmark_manager_test database in the feature and Bookmark tests.  
  - Make sure your feature and unit tests are passing.  
  - Update your database setup instructions to include the test database.

----------

## Day 3

### Goal Setting
- Update/clean-up Makers' Notes folder
- Research some previous gaps in knowledge and update progress

### Pairing
- Used capybara matcher ```have_link("Youtube", href: "https://www.youtube.com")```
- Debugging: did not put in a fail-safe for an invalid url, so website didn't work when adding "www.youtube.com" without "http://" at start.
- Completed a full-stack feature.
- Wrapped database data in program object, i.e. each row of the table became an instance of the Bookmark class.

-----------

## Day 4

### Goal Setting
- Research how to use gem with ```is_url?("https://www.youtube.com")``` or fail-safe alternative
- Complete 'Databases - Domain Modelling using CRC Cards' workshop (see [workshops](https://github.com/JKBero/Makers-Notes/blob/master/Workshops.md))

### Pairing
- ```is_url?("url")``` is in a gem called lapis_lazuli (documentation [here](https://github.com/spriteCloud/lapis-lazuli)). Did not use gem in the end; instead used a simpler form instead ```raise "Invalid url" unless url.start_with?("http://", "https://")```.  
- There are generally four actions you can take with persistent data:
  - Creating data
  - Reading data
  - Updating data
  - Deleting data
- CRUD application is one that creates, reads, updates, and deletes data. The majority of web applications are, essentially, CRUD applications.
- RESTful routes: Used ```method_override``` in Sinatra.   

*In Controller:*
```
enable :method_override  

delete '/bookmarks/:id' do
  Bookmark.delete(id: params[:id])
  redirect '/bookmarks'
end
```

*In View:*
```
<li class='bookmark' id="bookmark-<%=bookmark.id%>">
  <a href='<%= bookmark.url%>'> <%= bookmark.title %> </a>
  <form action='/bookmarks/<%=bookmark.id%>' method='post'>
    <input type='hidden' name='_method' value='DELETE'>
    <input type='submit' value='Delete'>
  </form>
</li>
```  
[Sinatra docs](http://sinatrarb.com/configuration.html):  

> **:method_override - enable/disable the POST _method hack**  
>  
> Boolean specifying whether the HTTP POST ```_method``` parameter hack should be enabled. When ```true```, the actual HTTP request method is overridden by the value of the ```_method``` parameter included in the POST body. The _method hack is used to make POST requests look like other request methods (e.g., ```PUT```, ```DELETE```) and is typically only needed in shitty environments – like HTML form submission – that do not support the full range of HTTP methods.  
> 
> The POST ```_method``` hack is implemented by inserting the ```Rack::MethodOverride``` component into the middleware pipeline.  

-----------  

## Day 5

### Goal Setting
 - Read through [REST](https://github.com/sjmog/rest) workshop
 - More research on DELETE/POST & method_override in Sinatra
 
### [Learning Objective Gaps - bookmark manager project](https://github.com/makersacademy/course/blob/master/bookmark_manager/learning_objectives.md)  
💛 Implement a RESTful routing convention.  
Turn routes like this: GET /show-bookmark-1 into routes like this: GET /bookmarks/1.  
💚 Validate in the model layer.   
Stop Bookmark.create from creating a bookmark record in the database if its URL is invalid.   
💚 Build a Registration system.   
Allow a user to sign up to an application through a clickable form. Also, encrypt their password.   
💚 Build an Authentication system.   
Allow a user to sign in to an application through a clickable form, using some details including their password.  
❤️ Implement a one-to-many relationship.   
Get all comments for a bookmark using SQL, or with a method like this: bookmark.comments.  
💛 Use the psql command to interact with PostgreSQL.  
Create a database in psql. Add a table. Add some records. Read those records.  
💛 Implement a many-to-many relationship.  
Get all tags for a bookmark using SQL, and all bookmarks for a tag using SQL, or with methods like this: bookmark.tags and tag.bookmarks.  
💚 Use Rake to automate environment tasks.  
Take a script you run from the command-line like this: ruby my_automation_script.rb and make it work when you do this: rake script:automate.  
💛 Test-Drive advanced Objects in Ruby, including adapter, wrapper, and service objects.  
Write a test for a Bookmark.create method that takes properties as arguments, and gives you back an object which exposes all those properties as attributes, and has an id attribute.  

-----------

## Weekend Challenge  

### Goal Setting 
- Work on the above learning objectives
  
------------------  
------------------  
  
  ## Gaps in Knowledge
  
| Knowledge gap | Resources read | Practicals/projects | Other | Understanding :vertical_traffic_light: |
| --- | --- | --- | --- | --- |
| [Encapsulation & Cohesion](https://github.com/makersacademy/skills-workshops/blob/master/practicals/object_oriented_design/encapsulation.md) | see [workshops](https://github.com/JKBero/Makers-Notes/blob/master/Workshops.md) | | read through practical | :green_book: |
| [Forwarding, Polymorphism](https://github.com/makersacademy/skills-workshops/blob/master/practicals/object_oriented_design/oo_relationships.md) | see [workshops](https://github.com/JKBero/Makers-Notes/blob/master/Workshops.md) | Practicals | | :green_book: |
| [Dependency Injection](https://github.com/makersacademy/skills-workshops/blob/master/practicals/object_oriented_design/dependency_injection.md) for testing in isolation | | Oystercard, Takeaway | Explained to colleague | :green_book: |
| [Entity Relationship Diagrams](https://github.com/makersacademy/skills-workshops/blob/master/practicals/databases/entity_relationship_diagrams.md) | see [workshops](https://github.com/JKBero/Makers-Notes/blob/master/Workshops.md)| Practical | | :green_book: |
| [Databases - Domain Modelling using CRC Cards](https://github.com/makersacademy/skills-workshops/tree/master/week-4/domain_modelling_student_directory_using_crc_cards) | see [workshops](https://github.com/JKBero/Makers-Notes/blob/master/Workshops.md) | Workshop exercise | | :orange_book: |
| [REST](https://github.com/sjmog/rest)| see [workshops](https://github.com/JKBero/Makers-Notes/blob/master/Workshops.md) | | | :green_book: |
| method_override in Sinatra & DELETE vs POST | Completion of REST above | | | :green_book: |
