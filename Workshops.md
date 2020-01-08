# Workshops

- ["Magic Numbers"](#magic-numbers)  
- [Single Responsibility Principle](#single-responsibility-principle)  
- [Encapsulation](#encapsulation)  
- [Polymorphism](#polymorphism)  
- [Debugging workshop](#debugging-workshop)  
- [TDD workshop](#tdd-workshop)  
- [Feedback workshop](#feedback-workshop)  
- [Process modelling workshop](#process-modelling-workshop)  
- [Empathy workshop](#empathy-workshop)  
- [Databases - Domain Modelling using CRC Cards](#databases---domain-modelling-using-crc-cards)  
    - [Entity Relationship Diagrams](#entity-relationship-diagrams)
- [RESTful Routes](#restful-routes)
- [Following the flow and getting visibility in JavaScript](#following-the-flow-and-getting-visibility-in-javascript)
- [The JS Event Loop](#the-js-event-loop)
- [Tech CV](#tech-cv)

### "Magic Numbers"

[Eliot Sykes' definition:](https://www.eliotsykes.com/magic-numbers)

> Magic numbers are hardcoded, unexplained values in code.
> To remove a magic number, introduce a Ruby constant. Constants have values that do not change (unlike variables which do change). Constants have SCREAMING_SNAKE_CASE names.
> Magic numbers cover any unexplained values, including strings, arrays, dates, regular expressions, and so on.  

-------------

### Single Responsibility Principle

[Medium definition:](https://medium.com/@severinperez/writing-flexible-code-with-the-single-responsibility-principle-b71c4f3f883f)  

> SRP states that every class or module in a program should have responsibility for just a single piece of that program's functionality. Further, the elements of that responsibility should be encapsulated by the responsible class rather than spread out in unrelated classes.  

-------------

### Encapsulation
[GeeksforGeeks description:](https://www.geeksforgeeks.org/ruby-encapsulation/)

> Encapsulation is defined as the wrapping up of data under a single unit. It is the mechanism that binds together code and the data it manipulates. In a different way, encapsulation is a protective shield that prevents the data from being accessed by the code outside this shield.
> - Technically in encapsulation, the variables or data of a class are hidden from any other class and can be accessed only through any member function of own class in which they are declared.
> - Encapsulation can be achieved by declaring all the variables in the class as private and writing public methods in the class to set and get the values of variables.
>
> Advantages of Encapsulation:
> - Data Hiding: The user will have no idea about the inner implementation of the class. It will not be visible to the user that how the class is storing values in the variables. He only knows that we are passing the values to a setter method and variables are getting initialized with that value.
> - Reusability: Encapsulation also improves the re-usability and easy to change with new requirements.
> - Testing code is easy: Encapsulated code is easy to test for unit testing.  
  
-----------  
  
### Polymorphism

[Back to Basics: Polymorphism and Ruby](https://thoughtbot.com/blog/back-to-basics-polymorphism-and-ruby)

> Polymorphism - the provision of a single interface to entities of different types.  
>   
> Polymorphism is one of the fundamental features of object oriented programming, but what exactly does it mean? At its core, in Ruby, it means being able to send the same message to different objects and get different results.

-------------
-------------

## Debugging workshop

Use: error message
1. Understand the problem (don’t take stabs in the dark)
2. Fix it

Bugs:
- Syntax Error; compiler (e.g. IRB) doesn’t know what went wrong
- Runtime Error; name error (haven’t declared the variable)
- Program not terminating; infinite loop / code hangs
- Unexpected results

Tighten the loop = find the right line / follow the stack trace
Get visibility = use ```p``` to get visibility on each line   
If you locate the issue, fix it  
Rerun the tests   
If they *don't* pass, revert the changes and restart the debugging process  

--------------
--------------

## TDD workshop
- Process of writing tests to guide the writing of code to meet user needs
- Why use it?
1. Helps break down the problem
2. Tests can serve as documentation (explaining what the code does / how it performs)
3. Tests: Act as a safety net, especially as the program gets larger

Term note: "production code" is the term used for code (often unfinished) you are showing to the client.

__Designing a piggy bank:__
- Define user needs
  - store money
  - destroy + taking all the money out
  - discourage people from taking it out
- Write user stories
- Choose one user story:
  - As a user  
    So I can save up money  
    I want to store it in a piggy bank
- Create domain model (objects/messages):
  
  | Objects | Messages |
  | ---- | ---- |
  | user | |
  | money | |
  | piggy bank | store() |
  
- Write a feature test:  

  ```ruby
  piggy_bank = PiggyBank.new   # =>NameError (unitialized constant PiggyBank)
  piggy_bank.store(1)   #maybe store needs to return a clink sound to confirm that the coin landed
  => 'clink'
  ```  
  
  - What is the behaviour of store method?
  
  |  Input | Output |
  | ---- | ---- |
  | 1 | 'clink' |
  | 2 | 'clink' |
  | 0 | nil |
 
- Create directory; create lib; create spec; create piggy_bank_spec.rb within spec
- Write rspec test  

```ruby
describe PiggyBank do
  describe "#store" do
    it "should return 'clink' when I store 1 pound" do
      piggy_bank = PiggyBank.new    # Or you can use "subject" instead; whatever you're comfortable with
      expect(piggy_bank.store(1)).to eq("clink")
    end  
        
     it "should return 'clink' when I store 2 pounds" do
       piggy_bank = PiggyBank.new
       expect(piggy_bank.store(2)).to eq('clink')
     end  
     
     it "should return nil when I store 0 pounds" do
       piggy_bank = PiggyBank.new
       expect(piggy_bank.store(0)).to eq(nil)
     end 
  end
end  
```  

  - Note: in rspec "describe", "it", and "expect" (matchers ".to eq" and ".to raise_error") are most important
  - Testing state vs testing behaviour
> Testing state means you're verifying that the code under test returns the right results. Testing interactions means you're verifying that the code under test calls certain methods properly.  

 - Make it pass (red-green-refactor)  
 
 ```ruby
 class PiggyBank
   def store(amount)
     "clink" if amount > 0
   end
 end  
 ```
 
  - Refactor (is this the most straightforward, readable way?)
  - Write another test for that method to further describe it's function (maybe the method does more things / test for outliers)
  
  - Address next user need
    - As a user
      So I can spend money
      I want to take money out of the piggy bank
    - Domain model: object = piggy bank, message = destroy
      
  - Feature test  
  
  ```ruby
  piggy_bank = PiggyBank.new
  piggy_bank.destroy
  => 0
  ```
      
  |  Input | Output |
  | ---- | ---- |
  | .store(1) | 1 |
  | .store(1).store(2) | 3 |
  | do nothing on new piggy bank | 0 |
  
  - Unit test
  
  ```ruby
  describe "#destroy" do
    it "should return 1 when I had stored 1 pound in it"
      piggy_bank = PiggyBank.new   #arrange
      piggy_bank.store(1)
      expect(piggy_bank.destroy).to eq 1   #assert( act ) ...
    end
  end
  ```
  
  - Pass test   
  
  ```ruby
  def destroy
  end
  ```
  - and so on....  
  
----------  
----------  

## Feedback workshop  

= Info about something / someone / behaviours, **which is used as a basis for improvement**

#### Why is it difficult?
**Love & Acceptance VS Learning & Growth**

- Questioning motivation
- Not all are trained / learnt the skill
- Not wanting to hurt someone (empathy or perhaps backlash)
- Fear of not being accepted
- Hard to receive, as perhaps very self-critical / feel threatening
- Hard to receive, as perhaps you have ego / pride
- Fear based behaviours

#### How can we make it easier?
1. Shift your perspective
- Do not view it as positive or negative... NEUTRAL (something to help YOU grow)
- See it as something kind
2. Empowered receiver
- Ask for it; be eager and specific; pairing culture / team culture
- Gatekeeper
- As a receiver FB helps us understand ourselves, profile, blind-spots #freetherapy
- Helps us practice assertiveness, boundaries, cultivate authentic and equal relationships
- Improve work life and overall quality of life
3. Know thyself
- 3 feedback triggers:  
  1. Truth trigger - seems wrong or off target
  2. Relationship triggers - something about our relationship with the person
  3. Identity triggers - undermines how we see ourselves ("Google bias")
4. Wrong-spotting - our default mindset is looking for what is wrong first
5. We all have blind spots

#### Building resilience
- What is your happiness set point? http://www.happiness-survey.com/
- Meditation increases your baseline happiness
- Swing: How wide do you swing?
- Recovery / Sustain: How long does it take for you to return to your baseline happiness? (minutes / hours / days...)

#### Understand feedback
- Appreciation - to acknowledge, connect, motivate, reassure, thank
- Evaluation - to rate or rank against a set of standards, aling expectation, inform decision-making
- Coaching - to help receiver expand knowlede, sharpen skill, improve capability

#### Use a framework
A - actionable (avoid adjectives like "good"/"bad")
S - specific (avoid stories; use hard facts)
K - kind (being direct can also be kind)

Communication stances - check your energy first.
- Doormat - openly agreeable, people-pleasing behaviour
- Sword - steamrolling, dominating, aggressive - doesn't create safe space for others
- Lantern - ask questions, drop all assumptions

NVC (Non-Violent Communication)  

| Expression |
| ---- |
| Observation: When I see/hear.... |
| Feeling: I feel... |
| Need: Because I need... |
| Request: Would you be willing...? |

- know your feelings
- know your needs  

- ask permission to give feedback, respect boundaries
- state the purpose of you FB
- give specific feedback
- be direct and respectful
- read someone's state. 

- Weigh it carefully; you can reject it if it's right to do so
- Strive for learning in the feedback

**Ultimately, it's all to help you grow and improve**. 

--------------
--------------

## Process modelling workshop

**Applied to HTTP request/response cycle**

Model = a visual representation
- Oversight of how things work
- Detailing relationships between systems & objects
- Helps save time/mistakes
- Good for team work
- Establish clear responsibilities

### Processes to model
#### Home page

(The code for the app we'll use in the workshop is here: https://github.com/makersacademy/process_modelling)

A user visits https://makers-cats.herokuapp.com/ in their browser and is shown this HTML:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Req/Res</title>
  </head>
  <body>
    <ul>
      <a href="list.html">a list</a>
      <a href="cats.html">a cat pic</a>
    </ul>
  </body>
</html>
```

What if the user mistyped this url? Try to include more details into your model.

#### Cat page

A user clicks the a cat pic link and is shown this HTML:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>a cat</title>
  </head>
  <body>
    <img src='cat.jpg'>
  </body>
</html>
```

Don't forget to model the cat.jpg request and response.

#### Mailing list page

A user clicks the list link and is shown this HTML:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>A list</title>
  </head>
  <body>
    <form action="thanks.html" method="POST">
      <input type="text" name="email">
      <input type="submit">
    </form>
  </body>
</html>
```

The user fills in their email address and clicks the submit button.

The user is sent to the thanks.html page and is shown this HTML:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Thanks page</title>
  </head>
  <body>
    <h1>Thanks!</h1>
  </body>
</html>
```

![HTTP diagram](https://user-images.githubusercontent.com/49643736/69631193-8a760680-1045-11ea-8f6e-3b558b34a5a9.jpg)

------------
------------

## Empathy workshop

- Imperative for teamwork
- Understanding the frustrations etc. of a customer
- Being able to use empathy to understand a market and create products to help them / suit their needs
- Empathy for yourself ("Would you say this to your friends?")

Book: *The 5 Dysfunctions of a Team*

**3 types of empathy:**
Affective - feeling emotionally with someone else but not driven to help in a certain way
Empathic concern - Consciously understanding and internalising the emotions of another person - driven to help or respond appropriately
Cognitive - consciously imagining how someone is feeling wihout internalising it. E.g. negotiations or doctors with patients.

**4 reasons why empathy may be missing:**
1. Anger - feel numb towards another's pain / we feel contempt due to resentment etc.
2. Protection - unconsciously feeling as though another's pain is like a "virus"
3. Identifying - "too close to home"/triggering
4. Fear of intimacy - being emotionally distant is easier; fear of vulnerability

**Training:**
1. "Just like me" - apart of a similar tribe / the commonalities
2. Metta Bhavana - loving kindness meditation; rewiring the brain for empathy
3. Empathetic Active Listening
    1. Reflect back
    2. Ask questions instead of give answers - "don't try to be interesting, try to be interested"
    3. Validate emotions (even if you disagree with their logic)
    4. Don't offer unsolicited advice
    5. Be present - 80/20

----------
----------

## Databases - Domain Modelling using CRC Cards  

**[Class Responsibility Collaborator (CRC) Models: An Agile Introduction:](http://agilemodeling.com/artifacts/crcModel.htm)**

> A Class Responsibility Collaborator (CRC) model (Beck & Cunningham 1989; Wilkinson 1995; Ambler 1995) is a collection of standard index cards that have been divided into three sections. A *class represents a collection of similar objects*, a *responsibility is something that a class knows or does*, and a *collaborator is another class that a class interacts with to fulfill its responsibilities*.  
> 
> Collaboration takes one of two forms: *A request for information or a request to do something*. For example, the card Student requests an indication from the card Seminar whether a space is available, a request for information. Student then requests to be added to the Seminar, a request to do something. Another way to perform this logic, however, would have been to have Student simply request Seminar to enroll himself into itself. Then have Seminar do the work of determining if a seat is available and, if so, then enrolling the student and, if not, then informing the student that he was not enrolled.

**Student** 

| Responsibilities | Collaborators |
| --- | --- |  
| Student number | Seminar |
| Name | |
| Address | |
| Phone number | |
| Enroll in a seminar | |
| Drop a seminar | |
| Request transcripts | |

### Example CRC & database structures:
- Short example [here](https://github.com/makersacademy/skills-workshops/blob/master/week-4/domain_modelling_student_directory_using_crc_cards/crc_example.md)  
- Workshop exercises [here](https://github.com/makersacademy/skills-workshops/tree/master/week-4/domain_modelling_student_directory_using_crc_cards).  
- Workshop solutions [here](https://github.com/makersacademy/skills-workshops/blob/master/week-4/domain_modelling_student_directory_using_crc_cards/COACH_INSTRUCTIONS.md).  

### [Entity Relationship Diagrams](https://github.com/makersacademy/skills-workshops/blob/master/practicals/databases/entity_relationship_diagrams.md)

> **One to one relationships**  
>  
> One Cohort has one SlackChannel.  
>   
> ![one-to-one](https://raw.githubusercontent.com/makersacademy/skills-workshops/master/practicals/databases/diagrams/one-to-one.png?token=AL2YBWH2FPMYDOGLWIVF2NK56I2ME)  
>   
> **One to many relationships**  
>  
> One Cohort has many Students.  
>   
> ![one-to-many](https://raw.githubusercontent.com/makersacademy/skills-workshops/master/practicals/databases/diagrams/one-to-many.png?token=AL2YBWCFP5IZAR6GNN5E4AC56I2VO)  
>   
> **Many to many relationships**  
>   
> A SlackChannel has many Students. A Student has many SlackChannels.  
>   
> ![many-to-many](https://raw.githubusercontent.com/makersacademy/skills-workshops/master/practicals/databases/diagrams/many-to-many1.png?token=AL2YBWCCDT2MAFDKWMLRUQC56IWZM)  
>   
> **Normalizing many to many relationships**
>   
> Slack Channels have many memberships. Students have many memberships.  
>   
> ![normalizing-many-to-many](https://raw.githubusercontent.com/makersacademy/skills-workshops/master/practicals/databases/diagrams/many-to-many2.png?token=AL2YBWC7LQQPE6QKKWT7NBS56IWZM)  

----------
----------

## RESTful Routes  

Source (along with useful online practice tool): [Rest](https://github.com/sjmog/rest/)

- The web is a network of **resources**, e.g. a bookmark stored as a row in a database.   
- **Representations** tie URLs to actions a user might want to take with these resources.  
- A representation is often a route to perform a specific action on a resource:
    - ```GET /bookmarks/1```  
    - ```GET /image.jpg```  
    - ```GET /index.html```  
- RESTful routing exposes the true nature of your web application: as a **state machine** capable of being in a finite number of different states. Movements between the states are determined by user interactions, and are called **state transitions**:  
    - Having 35 bookmarks (state) 
    - Adding a bookmark (state transition) 
    - Having 36 bookmarks (state)
- A well-designed application is a state machine. That is, it is a machine capable of being in various states.  
- Using GET, DELETE, POST and so on, with well-formed URIs, is the way that a user navigates through different states of the machine.  
- Each action the user takes returns a resource showing the next state of the application.  

### [POST vs PUT](https://restfulapi.net/rest-put-vs-post/)
> Generally, in practice, always use PUT for UPDATE operations.  
> Always use POST for CREATE operations.

----------  
----------  

## Following the flow and getting visibility in JavaScript  

- console.logging recognisable strings, e.g. within methods to figure out what code is running and in which order.
- ```console.log(this);```
- variable: ```console.log(airport);```
- function return values: ```console.log(airport.land());```
- function parameters: does this parameter contain what I expect? What does this parameter even contain?
```javascript
Airport.prototype.land = function(plane) {
    console.log(plane);
};
```  
- using a step debugger -> allows you to step through your program line by line. Can use in dev tools or Node. Up to personal preference. 
```javascript
function sayHi() {
    debugger;
    console.log("hi!");
};  

sayHi()
```  
- arity = number of arguments that a method takes.

#### Resources  
[Debugging pill](https://github.com/makersacademy/course/blob/master/pills/debugging.md)  
[The ready position](http://sjmog.github.io/posts/491_learning_to_learn_1/)

----------
----------

## The JS Event Loop

Research:  
Stack (LIFO last in first out) - add "frames" to call stack. From Message Queue to Call Stack cycle is called a "tick"  
Queue (FIFO first in first out)  
Asynchronous  
Non-blocking  
Multi-threaded  

How do you handle several asychronous calls that depend on each other? Can nest in code: nest a ```$.get()``` request within another ```$.get()``` request, but this was callback hell (goes on for ages and is very confusing). But there is a library called Promises which is now incorporated into JS - reads better. (Promise.all with Async/Await)

----------
----------

## Tech CV

Github CV - priority. Employment team use this to put candidates forward   
PDF/one page CV - needed for roles outside Makers https://enhancv.com/   

Describe who you are. 
- What is your interest in tech?
- Don't describe Makers.
- You can clarify at interview (re if you're junior); don't need it in CV.
- Why software development? What does this really mean to you?
- Show your previous background (diverse backgrounds are interesting).
- Soft skills: time management / team working

Next thing is: Projects (3 to 5)
- Make them look presentable
- Keep reviewing projects
- Pair with people to mock interview questions
- Keep a reflective on projects where possible esp team projects

Skills section (2 to 5)
- Choose one that's a little different if possible
- Core skills relevant to tech
- Thirst for knowledge is attractive (professional development)

Idea: implementation of new school system - uploaded everything; co-administrator to the system for all staff

Hobbies:
- keep it interesting
- also can mention any meetups etc.
