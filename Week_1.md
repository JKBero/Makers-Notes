# Week 1

[Day 1](#day-1)  |  [Day 2](#day-2)  |  [Day 3](#day-3)  |  [Day 4](#day-4)  |  [Weekend Challenge](#weekend-challenge)

**1. Test-drive a simple program using objects and methods**

**2. Pair using the driver-navigator style**

**3. Follow an effective debugging practice**

**4. Describe some basic OO principles like encapsulation, SRP**

## Day 1

### Debugging workshop  

Use: error message
1. Understand the problem (don’t take stabs in the dark)
2. Fix it

Bugs:
- Syntax Error; compiler (e.g. IRB) doesn’t know what went wrong
- Runtime Error; name error (haven’t declared the variable)
- Program not terminating; infinite loop / code hangs
- Unexpected results

Tighten the loop = find the right line  
Get visibility = use ‘p’ to get visibility on each line  
Follow the stack trace

### Reflection with pair partner (Boris Bike):  

#### 1. TDD
- We were diligent and methodical with writing tests before production code
(red-green-refactor).  

#### 2. Pairing
- We stayed positive and celebrated small successes
- We were patient with each other and allowed for different approaches /
experimentation. We did not interrupt each other
- We were both assertive with our ideas / explained concepts to each other
- We switched navigator / driver frequently  
__Improve:__
- ! Taking breaks more frequently

#### 3. Debugging
- Followed the stack trace
- Tried to identify the issue methodically
- We remained calm when we did not understand the source of the bug
- We googled and asked for help where appropriate   

### Gaps in knowledge to revisit:
- feature tests
- user stories -> Domain Model
- rspec syntax

## Day 2

### Goal Setting
- do some practicals
- review extra resources from yesterday's pairing project
- explain concepts outloud to someone  

| Knowledge gap | Resources read | Practicals/projects | Explain it outloud |
| --- | --- | --- | --- |
| feature tests vs user test | - [Boris Bikes Step 3 resources](https://github.com/makersacademy/course/blob/master/boris_bikes/3_from_domain_models_to_feature_tests.md)|  | Explained to Ellie |
| user stories -> Domain Model | - [Boris Bikes Step 2 resources](https://github.com/makersacademy/course/blob/master/boris_bikes/2_working_with_user_stories.md) |  | Explained to Ellie |
| rspec syntax | - [Boris Bikes Step 8 resources](https://github.com/makersacademy/course/blob/master/boris_bikes/8_back_to_the_unit.md)|  |  |
| debugging -> using the stack trace | - [Boris Bikes Step 4 resources](https://github.com/makersacademy/course/blob/master/boris_bikes/4_errors_are_good.md) |  |  |

### Reflection with pair partner (Boris Bike):  

#### 1. TDD
- We were diligent with feature tests, unit tests, writing code and repeating.
- More experience with breaking down user stories into Domain Models
- Improved understanding of Rspec syntax / format

#### 2. Pairing
- We celebrated small successes; kept it light and able to laugh together
- Very focused; were not distracted; covered a good number of steps at a healthy pace
- Kind assertion; not shy to share ideas, explain concepts / logic
- Learnt from each other; both were open listeners; both remained calm and professional
- Strong driver-navigator; navigators utilised their role as visionary and resource provider; frequent swapping; driver was allowed to drive
- We experienced a particular issue with Rspec error raising methods & Ruby fail/raise methods, but bounced ideas off each other, trying to dissect the logic, experimenting and ultimately learning from our mistakes/experiments; very collaborative
- Overall very smooth & enjoyable pairing experience

__Improve:__
- ! Make commits more often, after every peace of meaningful work
- ! Breaks more frequently
- ! Go home earlier; we were sucked into the above problem at the end and were eager to solve it, but past the point of being productive and were needing rest instead
- ! When I was driving, my pair had an excellent way of asking me helpful questions to steer me towards a solution, and not just telling me the solution. I would like to adopt this more in my approach as navigator with future partners.

#### 3. Debugging
- Following the stack trace and able to explain it outloud
- Used 'p' to get visibility
- Identified the issues methodically and remained calm
- Researched our own tools to address syntax and language issues

#### 4. OO Concepts
- Pair partner explained encapsulation to me and utilised it in our code.

> [GeeksforGeeks description:](https://www.geeksforgeeks.org/ruby-encapsulation/)
>
> Encapsulation is defined as the wrapping up of data under a single unit. It is the mechanism that binds together code and the data it manipulates. In a different way, encapsulation is a protective shield that prevents the data from being accessed by the code outside this shield.
> - Technically in encapsulation, the variables or data of a class are hidden from any other class and can be accessed only through any member function of own class in which they are declared.
> - Encapsulation can be achieved by declaring all the variables in the class as private and writing public methods in the class to set and get the values of variables.
>
> Advantages of Encapsulation:
> - Data Hiding: The user will have no idea about the inner implementation of the class. It will not be visible to the user that how the class is storing values in the variables. He only knows that we are passing the values to a setter method and variables are getting initialized with that value.
> - Reusability: Encapsulation also improves the re-usability and easy to change with new requirements.
> - Testing code is easy: Encapsulated code is easy to test for unit testing.

### Gaps in knowledge to revisit:
- [BDD cycle](https://github.com/makersacademy/course/blob/master/pills/bdd_cycle.md)
- Rspec error raising methods & Ruby fail/raise methods  

## Day 3

### Goal Setting
- complete 2 practicals
- read BDD cycle resource
- explain concept of encapsulation outloud to someone

## Day 4


## Weekend Challenge
