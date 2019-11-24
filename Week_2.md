# Week 2

[Day 1](#day-1) | [Day 2](#day-2) | [Day 3](#day-3) | [Day 4](#day-4) | [Day 5](#day-5) | [Weekend Challenge](#weekend-challenge) | [Gaps in Knowledge](#gaps-in-knowledge) 

[Feedback workshop](#feedback-workshop) |  [Domain Modelling workshop](#domain-modelling-workshop)

**1. Use all of week 1's skills (don't underestimate the importance of this)**  

**2. Break one class into two classes that work together, while maintaining test coverage**  

**3. Unit test classes in isolation using mocking**  

**4. Explain some basic OO principles and tie them to high level concerns (e.g. ease of change)**  

**5. Review another person's code and give them meaningful feedback**

---------

## Day 1

### Goal setting
- attend peer code review workshop
- look over gaps in knowledge

### Reflections

#### 1. Week 1 skills
- Continued practise of TDD, SRP, DRY etc, through Airport & Oystercard. Noticed that testing & coding Oystercard is so much faster now.

#### 3. Mocking
- Tackled with this in Airport challenge, and came to a good understanding of isolation tests, using doubles/stubs.
- Was able to explain these concepts to others - Kealan, Ellie, Danny

#### 5. Review others' code
- Kealan & Ellie reviewed my Airport code: good suggestions given / questions asked. Kealan pointed out I could refactor ```@in_journey == true``` to just ```@in_journey``` as it will still return true - great reminder.
- Ellie helped with a clearer understanding of ```attr_reader``` & ```def initialize``` 

----------

## Day 2

### Goal Setting
- attend Feedback workshop
- research gaps in knowledge from Oystercard

### Reflections

#### Feedback
- Danny and I practised giving feedback after our pairing session:
 - Strong communication; sharing ideas and explaining our logic to each other
 - Danny shared I have strong teaching skills; able to explain concepts well and bring them across to others
 - Patient and friendly approach; very smooth with good rapport & trust between us
 - Made a lot of progress; strong focus and team work
 - Not relevant to this session or our relationship, but could imagine that when working with other personalities, we could both be more quiet when navigating and allowing the driver to figure out the writing/syntax as they go, although the sharing of ideas was strong.

----------

## Day 3

### Goal Setting
- attend Domain Model workshop
- research gaps in knowledge from Oystercard

### Reflections

#### 2. Break one class into two classes
- Use ```p``` more for visibility in tests
- Building on domain modelling skills; helps with clarity for purpose of classes & methods

-----------

## Day 4

### Goal Setting
- Research dependency inversion and implement in Oystercard


-----------  

## Day 5

### Goal Setting


-----------

## Weekend Challenge  

### Goal Setting 

  
------------------  
------------------  
  
  ## Gaps in Knowledge
  
| Knowledge gap | Resources read | Practicals/projects | Other |
| --- | --- | --- | --- |
| Installing and upgrading gems using Bundler | | Oystercard | Talked through with Ellie |
| Explain the structure of a Gemfile | | Oystercard | Talked through with Ellie |
| What do default options in RSpec configuration file mean? | | | |
| What's a class constructor? What is the initialize method? How are they different? | | Boris Bike, Airport, Oystercard | Talked through with Ellie |
| When do you have to use a return statement in Ruby and when can you omit it? | | experimented in IRB | Talked through with Ellie |
| What are instance variables and how are they different from local variables? | | | Talked through with Ellie |
| What are exceptions in Ruby? Why do they have messages associated with them? | http://rubylearning.com/satishtalim/ruby_exceptions.html | Boris Bike, Airport, Oystercard | Alistair explained it |
| How can you check an expression raises an error with RSpec? Why do you have to pass the code as a block to do this? | https://stackoverflow.com/questions/21567838/when-to-use-curly-braces-vs-parenthesis-in-expect-rspec-method  "As for rules, you pass a block or a Proc if you're trying to test behavior (e.g. raising errors, changing some value). Otherwise, you pass a "conventional" argument, in which case the value of that argument is what is tested." | | Talked through with Ellie |
| UML (link in debugging workshop) | | | |
| Dependency Inversion Principle | http://www.getlaura.com/dependency-inversion-principle-in-ruby/ | Oystercard | | 
| Using APIs | | Takeaway challenge | |
