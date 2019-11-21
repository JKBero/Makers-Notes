# Workshops

["Magic Numbers"](#magic-numbers) | [Single Responsibility Principle](#single-responsibility-principle) | [Encapsulation](#encapsulation)

[Debugging workshop](#debugging-workshop) | [TDD workshop](#tdd-workshop) 

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

Tighten the loop = find the right line  
Get visibility = use ‘p’ to get visibility on each line  
Follow the stack trace  

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

  ```
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
  describe "#destroy" do
    it "should return 1 when I had stored 1 pound in it"
      piggy_bank = PiggyBank.new   #arrange
      piggy_bank.store(1)
      expect(piggy_bank.destroy).to eq 1   #assert( act ) ...
    end
  end
  ```
  
  - Pass test   
  
  ```
  def destroy
  end
  ```
  - and so on....  
  
  -------------  
  -------------
  
  
