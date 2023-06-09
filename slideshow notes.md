# OOP

### OOP Overview

Object Oriented Programming = programming paradigm that focuses on creation of custom classes for special objects

### Basic Terminology

Class = abstract description of new objects that can be made (contains attributes and methods)

Attributes = variables/data belonging to the class

Methods = functions the object can use/call for computation

Object = instance of class that can be used in a program

↳ Objects may have access to attributes and methods in that class.

iterable objects = objects iterable through (like a sequence)

eg. strings, lists, sets, dictionaries

↳ for loops can be used to access individual values without indexing

Note: The portion of the iterable object must be a sequence. Iterable doesn’t always mean indexable. 

# OOP 2

Encapsulation = hiding information (restricting access to certain classes/object’s attributes and methods)

<aside>
💡 Why? 
↳ Data protection
↳ Restricting certain methods (to be callable)

</aside>

In Python, there are no “public”/“private” methods, therefore we use this special system to hide attributes and methods

__ double underscore prefix indicates encapsulation!

```python
#python example
class Student:
  def __init__(self,nameF, nameL, num):
    self.firstName = nameF
    self.lastName = nameL
    self.__studentNumber = num
  
  def __getStudentNumber(self):
    return self.__studentNumber
#end of Student
s1 = Student("Mr.", "Park", 10)
print(s1.__getStudentNumber()) # Will cause an error
print(s1.__studentNumber) # Will also cause an error
```

Importance of encapsulation

```python
class Student:
  def __init__(self,nameF, nameL, num):
    self.firstName = nameF
    self.lastName = nameL
    self.__studentNumber = num

#end of Student

s1 = Student("Mr.", "Park", 10)
print(s1.firstName) # Returns/Outputs “Mr.”

s1.firstName = "Ms."
print(s1.firstName) # Returns/Outputs “Ms.”
```

It is **common practice** to use a setter + a getter to control how encapsulated code is set. 

For example, it can be for preventing others from changing passwords. 

↳ setter = sets how code is allowed to be accessed (by other parties)

↳ getter = retrieves a value

```python
class Student:
  def __init__(self,nameF, nameL, num):
    self.__firstName = nameF
    self.__lastName = nameL
    self.__studentNumber = num
   
# -> setter 
  def setFirstName(self, newName):
    self.__firstName = newName
    
# -> getter
  def getFirstName(self):
    return self.__firstName
```

## Overrides and Polymorphism

Overriding = multiple methods in different classes w/ same method name + parameters

↳ can also override built-in magic methods OR base functions (eg. __init__, __str__)

↳ One method is in the parent class + one in child class (see OOP 3)

This allows the child class to provide specific implementation for a method that exists in the parent class.

Overloading* = multiple methods within one class w/ same method name but different parameters 

*does NOT exist in Python 3

Polymorphism = A method that can be used across different classes and objects that is dependent on parameters

- Different classes (non-inherited) can have the same named methods (Simple) → Polymorphism
- Within a set of inherited classes have the same methods

- eg. two difference classes with the same method
    
    ```python
    class Bear:
        def sound(self):
            print("Groarrr")
     
    class Dog:
        def sound(self):
            print("Woof woof!")
     
    def makeSound(animalType):
        animalType.sound()
    
    bearObj = Bear()
    dogObj = Dog()
     
    makeSound(bearObj)
    makeSound(dogObj)
    
    “”” In Conclusion:
    We can give two different classes same methods; hence, Polymorphism.
    “””
    ```
    

Overloading is illegal in Python 3, but is a type of polymorphism!

Inherited Classes modifying inherited methods (overriding) → polymorphism in Python 3

Base Overrides

**Override and Polymorphism with Python**

We can have:

- Two different classes have a same attributes and methods
- A child of a parent have an ***overrided*** method where the child would utilize the method differently.

These are the **two fundamental** concepts of overriding and polymorphism in Python.

If we we can override a **built-in methods/operators** that we use in Python 3 as well for our own objects.

*Some website calls them “magic methods”*

- Example
    
    ```python
    class Dog:
    	def __init__(self,name):
    		self.__name = name
    	
    	def __str__(self):
    		return “Woof, I’m %s.” % self.__name
    
    corgi = Dog(“Tobasco”)
    print(corgi) → “Woof, I’m Tobasco.”
    ```
    
    Why override built-in methods and operators?
    
    **Benefits:**
    
    - Can start to complete mathematical operations on custom Objects
    - Can start to compare equality between custom Objects
    
    **Therefore:** You can start to manipulate how the Object behaves when met with built-in methods and operators
    
    ## **__repr__() base function**
    
    **When we try to make our custom objects printable, we actually need to override __repr__ and __str__**
    
    **__repr__** → Allows us to present a printable version of our object
    
    **__str__** → Allows us to convert our object to a string
    
    Coding Notes
    
    - __ in front of methods = encapsulation, meaning they are private attributes
    - in __init__, the purpose is to create attributes - all attributes should be simple. If needed to be modified, modify a method in the attribute, but don’t make the initialization complex.
    
    Custom Class assignment 
    
    - Need to encapsulate
    - THESE TWO LINES MUST BE IN YOUR CODE
    
    ```python
    def __str__(self_:
    	#base override of string built-method
    	return f'User: {self.__username}'
    
    def __repr__(self):
    	return eslf.__str__()
    #end of user
    ```
    
    Test
    
    - don’t need to encapsulate
    
    Personal Project
    
    - don’t need to encapsulate

# OOP 3

## inheritance maowowoow 😽

********************************inheritance:******************************** when object or class is based on another class; features are from a *parent class*

### flaws of inheritance

→ if parent class has a mistake, the child class will also be messed up

**Types:**

- single inheritance ( a subclass inheriting the features of a single siperclass/parent)
- multiple inheritance (subclass inheriting the features of multiple parent classes)
- multilevel inheritance (subclass inheriting from another subclass; eg. A → B → C)

<aside>
📢 inheritance can have a hierarchy(branching like a tree) or be like a hybrid(mixing all types of inheritance)

</aside>

What can be done with inheritance?

- Child receives all attributes/methods of parent
    - can then enhance itself with new attributes/methods
- A child can **OVERRIDE** attributes and methods for their own liking/speciality

### single inheritance

```python
class ParentClassName:
	“”” Define Parent Class “””
	.
	.
	.

class InheritanceClass(ParentClassName):
	“”” Define Inherited Class “””

	def __init__(self, param, param2):
		ParentClassName.__init__(self, param)
		self.param2 = param2
```

### parent class and inheritance class

```python
#parent class
class Person:
  def __init__(self, name):
  	self.__name = name 
  
  def getName(self):
    return self.__name

#inherited class
class Student(Person):
  def __init__(self, name, num):
    Person.__init__(self, name)
    self.__sNum = num
  
  def getStudentName(self):
    return("%s: %s" % (self.__sNum,self.getName()))

#execution 
p = Person(“Mr. Park”)
s = Student(“Random Child”, “1234”)
print(p.getName()) # Output: “Mr. Park”
print(s.getStudentName(), “and” , s.getName()) # Output: “1234: Random Child and Random Child”
```

### what is super()?

built in method for classes to refer to their parent classes

- prevents from doing ParentClass.method(self)
- The self with self gets confusing

### multiple inheritances

1) Multi-generational

Grandparent → Parent → Child

2) Multi-parent (not lmited to 2)

(Parent A + Parent B) → Child

3) Mixture of 1 and 2

### polymorphism

- a method that can be used across different classes and object that is dependent on its parameters
    - Different Classes (non-inherited) can have the same named methods (Simple) → Polymorphism
    - Within a set of inherited classes have the same methods

in inherited classes:

```python
class Parent:
	def method(self):
		pass

class Child(Parent):
	def method(self):
		# something different
		# Polymorphed to something else…
		# Same method name!
		pass
```
