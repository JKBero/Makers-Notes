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
- ! Debrief at every 45 min slot (set a timer)
- ! Brief at the start on what you're trying to improve, so they can keep you accountable

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
- complete 2 practicals working on TDD & debugging
- read BDD cycle resource
- explain concept of encapsulation outloud to someone
- pairing: share with partner at the start of your session, what you want to improve, and ask for feedback at the end/after 45 min session slots
- research SRP

### TDD workshop  
- Process of writing tests to guide the writing of code to meet user needs
- Why use it?
1. Helps break down the problem
2. Tests can serve as documentation (explaining what the code does / how it performs)
3. Tests: Act as a safety net, especially as the program gets larger

Term note: "production code" is the term used for code (often unfinished) you are showing to the client.

__Designing a piggy bank:__
- Define user needs
  - store money
  - discourage people from taking it out
  - destroy + taking all the money out
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
  - > piggy_bank = PiggyBank.new   # =>NameError (unitialized constant PiggyBank)
  - > piggy_bank.store(1)   #maybe store needs to return a clink sound to confirm that the coin landed
  - => 'clink'
  - What is the behaviour of store method?
  
  |  Input | Output |
  | ---- | ---- |
  | 1 | 'clink' |
  | 2 | 'clink' |
  | 0 | nil |
 
- Create directory; create lib; create spec; create piggy_bank_spec.rb within spec
- Write rspec test  

```
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
 
 ```
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
  
  ```
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
  
  ```
  
  ```

## Day 4


## Weekend Challenge
