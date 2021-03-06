# java-minimalist-convention

By default:

 1. Do not use primitives, use wrapper classes .
    * Forget about equals, and == problem. Equals will be used everywhere.
    * Forget about 0 and null problem for primitives.
    * Everything is an object. Right?
    * Scala does not have primitives.
    
 2. Do not use checked exceptions, create your own response objects or use Java 8 Optional class.
    * throws clause  for each method is hard to read.
    * Checked exceptions violate OCP.
    * In java 8 you cannot map, filter etc on function with checked exception, this leads to rethrowing, and noisy code.
    * Using checked exceptions for flow control (app logic) usually leads to poor desing.
    * C# (and any other language) does not have checked exceptions.
    * Check Effective Java Item 59: Avoid unnecessary use of checked exceptions.

 3. Minimize the use of runtime exceptions, create your own response objects or use Java 8 Optional class.
    * Dont Use Exceptions For Flow Control.
    * Use standard runtime exceptions as much as possible.
    
 3. If you want to extend a class... (do not use abstract class or ordinary class, use composition and interfaces)
    * Try to decouple class into smaller clasees. Use composition over inheritance.
    * Use Interface instead of abstract class (especially, starting from java 8).
    * If you cannot apply two mentioned options, then use abstract class, and only then ordinary class (probably this will lead to poor design).
    * Check Strategy pattern.
    * Check Factory pattern.
    * Go(golang) does not have classes, only interfaces.
    
 4. Do not use arrays, use collections.
    * Array is almost same as primitive (check point 1).
    * In long term, you will reach the point when you will convert array to list.
    * There is no clause when to use array, except optimization.
    * Array is not used in many higher order languages.
    
 5. Do not use switch construct.
    * Switch is big and ugly.
    * Remember when you forgot to add break? Do not write code which leads to errors.
    * If construct offers totaly same functionality.
    * For instance:
      * public Animal returnWhithoutSwitch(String animalString){
      *   if(someString.equals("wolf")) return new Wolf();
      *   if(someString.equals("rabbit")) return new Rabbit();
      *   if(someString.equals("fox")) return new Fox();
      * }
      
 6. Do not use for and foreach construct.
    * Use collections streams, learn how they work and how do the labmdas work. They are shorter.
 
 7. Do not use protected keyword (same for default accessability).
    * I have never had a situation where it was useful.
    * Most of the languages does not have such accessability modifiers.
    * IMHO, class should have only internal and external presentation. Class is a black box with input and output wires.
    
 8. Readability over OOP sophistication and code size.
    * Work towards DSL, code you write must be human readable and intuitive.
    * If you want to choose some design pattern over readability, then you are probably doing a mistake.
    * If you want to insert a hack or make variable name shorter, which makes code unreadable, then you are probably doing a mistake.
    * If you have to choose between very small hack and introducing desing pattern (or chain of desing patterns), 
      then personally, I would choose hack because overengineered solution is harder to read (probably you will introduce more classes, so I will have to click a lot:). IMHO.
    * If desing pattern eases the readability of complex class, then introduce it.  
    * Learn SOLID and desing pattens. Readability does not mean that you should not be an expert in OOD.
 
 9. Do not use commas and labels.
 
 10. Keep away from creating your custom annotations. Try to use lambdas.
    * Annotations are hard to debug.
    * Annotations are hard to test.
    
 11. Do not use inner classes.
    * C# does not have them.
    * Hard to read.
 
Testing pitafalls:

 10. Do not use interfaces for testing purposes (only for polymorphic calls).
    * This bloats the code.
    * You have mockito for that.
    * For example, extracting DAO interface only for testing is plain stupid.
  
 11. Testing.
    * Tests should be fast.
    * As little mocking as possible. (We test real application, not your mocks)
    * Mocking is a smell of bad design.
    * Unit tests for internal business logic.
    * Integration tests to speak with external stuff (database).
    * Functional tests(Selenium, direct JSON request to your application) only to test that the basic functionality is working. Skip complex cases.
    * Create functional tests as well as integration tests as little as possible. Especially functional.
    
(they bloat the code, make it hard to read + usually you will end with flow based on exceptions)
