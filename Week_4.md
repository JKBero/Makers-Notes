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

-----------  

## Day 5

### Goal Setting


-----------

## Weekend Challenge  

### Goal Setting 

  
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
| [REST](https://github.com/sjmog/rest)| | | | |
| method_override in Sinatra & DELETE vs POST | | | | :closed_book: |
