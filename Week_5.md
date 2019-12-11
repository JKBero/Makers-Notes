# Week 5

[Day 1](#day-1) | [Day 2](#day-2) | [Day 3](#day-3) | [Day 4](#day-4) | [Day 5](#day-5) | [Weekend Challenge](#weekend-challenge) | [Gaps in Knowledge](#gaps-in-knowledge) 

**1. Test drive a simple front-end web app with Javascript**
  - Can you read and write JavaScript syntax?
  - Can you understand the rules that govern the behaviour fo the ```this``` keyword?
  - Can you follow the flow of an Ajaz request and response?
  - Can you follow the flow of control through code that uses callbacks?
  - Can you encapsulate behaviour in JavaScript?
  - Can you get visibility effectively in JavaScript?  ```console.log();```
  - Can you TDD in JavaScript?
  - Can you follow the flow of control over the whole web app cycle?
  
**2. Follow an effective process for learning a new language**  

---------

## Day 1

### Goal setting
- Research ORMs (object relational mappers, like Active Record)
- Research ```this``` keyword in Javascript
- Research AJAX (Asynchronous JavaScript And XML). Just a term for using Javascript a certain way. (XML is a markup language.)
- Research JSON (JavaScript Object Notation): encoding a hash/array etc into a string, that can be sent over http request and decoded at the other end.
- Rewrite fizz buzz in JavaScript  

### Practical: [Learning a new language by translation](https://hackmd.io/kMNgXiPHQf2Q_P9A-tnS9A)  

**Super handy: [Learn X in Y minutes - JavaScript](https://learnxinyminutes.com/docs/javascript/)**

| Ruby terms | JavaScript equivalent |
| ----- | ---- |
| classes ```class Object``` | prototype ```function Cat(name, age) {};``` |
| variables ```hat = []``` | ```var hat = []```|
| variable naming in snake case ```my_hats``` | camel case ```var myHats``` |
| arrays ```[2, 3, 'Four']``` | ```var arr = []``` |
| hashes ```{key: topping, value: pineapple}``` | ```{}``` |
| add new key & value to hash ```hash[:topping] = "pineapple"```  | ```hash.topping = "pineapple"``` |
| addition ```2+2``` | same |
| subtraction ```2-1``` | same |
| multiplication ```2*2``` | same |
| modulus ```2%4``` | same |
| iteration ```.map``` ```.each``` | ```[].forEach(function(n){});``` |
| methods ```def say_hello``` | function ```function hello() { };```|
| method naming ```def increase_temperature``` | ```Thermostat.prototype.increaseTemperature = function() { };``` |
| method naming with ? ```def purebreed?``` | ```isPurebreed``` |
| private methods in class ```private``` | ```Banana.prototype._myPrivateMethod``` |
| print ```puts``` ```print``` ```p``` | ```console.log();``` |
| instance variables ```@id``` / attr_reader ```attr_reader :id``` / initialize ``` def initialize(id:)```  | ```this.id = id;```  |
| method within class ```def hello ... end ``` | ```this.meow = function() { };```|
| ```self``` | ```this``` |
| create instance of class ```Cat.new("Tibs")``` | ```new Cat("Tibs")``` |
| conditionals ```if ... else ... end``` ```unless```| ```if (condition) {} else if (condition2) {} else {};```|
| comparitors ```==``` ```>``` ```<=```| ```==``` compares any types, so ```1 == '1'``` is true, ```===``` doesn't compare different types, so ```1 === '1'``` is false |
| booleans ```true``` ```false``` | Examples of expressions that can be converted to false are: ```null;``` ```NaN;``` ```0``` empty string (```""``` or ```''```) |
| negation ```!``` | same |
| and / or ```&&``` / ``` \|\|``` | same |
| converst to string ```to_s``` | ```toString()```|
| convert to string to integer ```to_i```| ```parseInt(string, 10)```  where 10 is the base number i.e. radix |
| convert to symbol ```to_sym``` | ```Symbol()``` |
| ```return``` | same |
| raise error ```raise``` ```fail``` | ```throw``` |
| switches ```case ... when ... end``` | ```switch(expression) { case x: ... break; case y: ... break; default: ... }``` |
| falsey values | [Source:](https://flatironschool.com/blog/javascript-vs-ruby) "Like in Ruby, null (in Ruby, it’s nil) and false will return false, however, some truthful values in Ruby will return false in JavaScript, like 0, empty strings (“”), and undefined." |
| one liner assignment | ```var person = "John Doe", carName = "Volvo", price = 200;```|
| increment ```+= 1``` | ```++``` |
| decrement ```-= 1``` | ```--``` |
| to the power of ```**``` | same |
| | ```typeof 3``` returns 'number' |
| string interpolation ```"Hello, #{person}"``` | ``` `Hello, ${person}` ``` Note: have to use backs ticks |
| constants ```MY_TOTAL = 10``` | there are no constants, they can be changed ```Poker.prototype.MY_TOTAL = 10;```, ES6: ```const MY_TOTAL = 10;```|
| scope of variables | If you leave the ```var``` keyword off, you won't get an error... but your variable will be created *in the global scope*, not in the scope you defined it in. |

----------

## Day 2

### Goal Setting
- Continue from Day 1's goals

----------

## Day 3

### Goal Setting
- Attend all workshops

### Q&A session  

- EcmaScript (e.g. ES6) -> formalising of different JavaScript versions  
- Prototypes / constructor() -> ways to deal with inheritence in JS  
- ```this```
  - inheritance of scope (similar to binding in Ruby). Ruby blocks are closures, JS {} are closures.
  - JS object is similar to a Ruby hash. ```this.name = name``` creates a key with an attached value.
  - Ruby object is a reference to a class and instance variables  
- JS has local and global variables -> read about variable scope and closures
- To require different JS files -> pull them all into a central html file with ```<script> </script>```
- NodeJS runs on the server (to be covered down the line)

### LinkedIn workshop
- Make yourself searchable/findable by putting keywords in (for visitors and recruiters)
- State any languages you know / are learning
- Add GitHub CV / one-page CV
- Profile:
  - Software Developer/Engineer (don't use junior until that's your actual role title); you can be more specific if that's what you are aiming for, i.e. Phython Software Developer
  - relevant "key" keywords
  - Check out other people's profiles
- Education & Experience:
  - Makers course
  - voluntary work
  - key education & work experience
- Recommendations:
  - use cohort connections etc.
- Use posts strategically / be interactive / connect -> blogs, online profile etc.
- Etiquette with reaching out to contacts
  - See if a Maker works there and reach out
  - Keep it casual; helps if you have already met briefly etc.
  - When starting out, look for jobs with companies who are already warm to Makers and are familiar with bootcamps.
  - Positivity is the best way to reach out; e.g. you heard them do a talk, do reach out and feedback on that. Later, if they're hiring, you have a connection.
  - Be respectful and conscious that people and hirers can be time poor.

-----------

## Day 4

### Goal Setting
- 

-----------  

## Day 5

### Goal Setting
- 

-----------

## Weekend Challenge  

### Goal Setting 

  
------------------  
------------------  
  
  ## Gaps in Knowledge
  
| Knowledge gap | Resources read | Practicals/projects | Other | Understanding :vertical_traffic_light: |
| --- | --- | --- | --- | --- |
| ORM | | | | :closed_book: |
| AJAX | | | | :closed_book: |
| | | | | |
| | | | | |
