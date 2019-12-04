# Week 1

[Day 1](#day-1) | [Day 2](#day-2) | [Day 3](#day-3) | [Day 4](#day-4) | [Weekend Challenge](#weekend-challenge) | [Gaps in Knowledge](#gaps-in-knowledge) 

**1. Test-drive a simple program using objects and methods**

**2. Pair using the driver-navigator style**

**3. Follow an effective debugging practice**

**4. Describe some basic OO principles like encapsulation, SRP**

---------

## Day 1

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

----------

## Day 2

### Goal Setting
- do some practicals
- review extra resources from yesterday's pairing project
- explain concepts outloud to someone  

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
- Pair partner explained encapsulation to me and utilised it in our code (see [Workshops](https://github.com/JKBero/Makers-Notes/blob/master/Workshops.md)).  

### Gaps in knowledge to revisit:
- [BDD cycle](https://github.com/makersacademy/course/blob/master/pills/bdd_cycle.md)
- Rspec error raising methods & Ruby fail/raise methods  

----------

## Day 3

### Goal Setting
- complete 2 practicals working on TDD & debugging
- read BDD cycle resource
- explain concept of encapsulation outloud to someone
- pairing: share with partner at the start of your session, what you want to improve, and ask for feedback at the end/after 45 min session slots
- research SRP
  
### Reflection on pairing (Boris Bike):  

#### 1. TDD
- Deeper understanding of TDD & feature vs unit testing
- Smoother and quicker writing in Rspec
- Improved at naming commits and tests

#### 2. Pairing
- A very calm and smooth session; driver-navigator roles respected
- Focused and achieved a good number of steps
- Discussion flowed easily; we understood each other's logic
- Briefed on what we wanted to get out of the session at the beginning, and held each other accountable
- Implemented debriefing at 45 min slots to reflect on the session so far
- Made regular commits at every red-green-refactor
- Ended the session at a healthy time; did not feel fatigued by the end

__Improve:__
- ! Perhaps more breaks, but this was improved compared to previous days

#### 3. Debugging
- Process of debugging was getting quicker
- Able to follow stack trace, line numbers and explain errors outloud

#### 4. OO Concepts
- The project covered "magic numbers" and SRP (see [Workshops](https://github.com/JKBero/Makers-Notes/blob/master/Workshops.md)).

-----------

## Day 4

### Goal Setting
- work on Birthdays practicals working on TDD & debugging
- read BDD cycle resource
- explain concept of encapsulation outloud to someone

#### 1. TDD

In our weekly cohort retrospective we queried **testing behaviours vs state**, and I have an improved understanding: Testing the actual end results, rather than testing the implementation within the program / the tools you've used. That way, if you or another developer make changes to the implementation, the tests will still pass because they are based on the results you were specifying.

A coach helped me implement this in my Birthdays project, by **mapping out what input & output you expect to see:**

Tests that it successfully stores something, with the output/result being itself. In the 'expect' line, it includes the implementation of arrays and hashes (i.e. partially tests state):

```
describe "#add_birthday" do
    it "stores one name and birthday" do
      new_list = BirthdayList.new
      expect(new_list.add_birthday("Sam", "19/06/1991")).to eq [{name: "Sam", birthday: "19/06/1991"}]
    end
end
```

The coach's test is more specific and returns a message in the form of a symbol ':success'. Now, if the implementation changes, the test still passes because it only tests behaviour:

```
    it "returns :success if given 'Sam' and '19/06/1991'" do
      new_list = BirthdayList.new
      expect(new_list.add_birthday("Sam", "19/06/1991")).to eq :success
    end
```

Change the code to include the ':success' message:

```
  def add_birthday(name, birthday)
    @list << {name: name, birthday: birthday}
    :success
  end
```  

#### Other

Getting started was the hardest part: While tackling the Birthdays project, I spent an half hour trying to understand where to start with the building process. That was the most time-consuming. I ran a **feature test** to help me understand, and **almost immediately this highlighted the beginning structure of the program.** From there onwards, it was a smooth process of practicing TDD; adding features and modifying the implementation each step of the way, with the tests guiding the simplest structure possible.

-----------

## Weekend Challenge  

### Goal Setting
- write a thorough README in the Airport Challenge - COMPLETED
- get as far as possible in the Airport Challenge - COMPLETED
- stick to TDD principles - COMPLETED
  
------------------  
------------------  
  
## Gaps in Knowledge
  
| Knowledge gap | Resources read | Practicals/projects | Other | Understanding |
| --- | --- | --- | --- | --- |
| feature tests vs user test | [Boris Bikes Step 3 resources](https://github.com/makersacademy/course/blob/master/boris_bikes/3_from_domain_models_to_feature_tests.md)| Boris Bikes, Birthdays, Airport Challenge | Explained to Ellie + TDD workshop | Green |
| user stories -> Domain Model | [Boris Bikes Step 2 resources](https://github.com/makersacademy/course/blob/master/boris_bikes/2_working_with_user_stories.md) | Boris Bikes, Airport Challenge | Explained to Ellie | Green |
| rspec syntax | [Boris Bikes Step 8 resources](https://github.com/makersacademy/course/blob/master/boris_bikes/8_back_to_the_unit.md)| Boris Bikes, Birthdays, Airport Challenge | Help from coach, retrospective | Green |
| rspec raise_error & ruby fail/raise methods | | Boris Bikes, Airport Challenge | | Amber |
| debugging -> using the stack trace | [Boris Bikes Step 4 resources](https://github.com/makersacademy/course/blob/master/boris_bikes/4_errors_are_good.md) | Boris Bikes, Birthdays, Airport Challenge | Debugging workshop | Green |
| [BDD cycle](https://github.com/makersacademy/course/blob/master/pills/bdd_cycle.md) | | | | Red |
| more familiarity with README structures | | Airport Challenge | | Red |
| difference between attr_reader & def initialize | | Airport Challenge | Explanation from Ellie & Danny & experimentation | Green |
| how does test coverage work in simplecov? | | Airport Challenge | Explanation from coach & experimentation | Green |

