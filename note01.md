#object oriented programming: notes 1
 
I think OOP is awesome :^)

```python
#example class

class Person:
    def __init__(self, name):
        self.name = name
        
    def __str__(self):
        return f"Person Object called: {self.name}"
      
    def __repr__(self):
        return self.__str__()
```
