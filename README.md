# giaic-6-Build_Compose_and_Decorate_A_Complete_Traditional_OOP_Practice_Series
Build_Compose_and_Decorate_A_Complete_Traditional_OOP_Practice_Series

**self ek special keyword hota hai jo current object ko refer karta hai.**

- Jab hum kisi method ke through object ke attributes (name, marks) ko access karte hain, tab hum self.name aur self.marks likhte hain.

### class Variable kya hota hai?
- 🟡 Ek aisi value jo sab objects ke liye common hoti hai.
class Counter:
    count = 0  # ← yeh class variable hai

   jaise self object ke liye hota hai, waise cls class ke liye hota hai.

### Class Method kya hota hai?
- 🔵 Ek method jo *object* ke bajaye **class** pe kaam karta hai.
- Isko banate waqt **@classmethod** likhna padta hai
- Aur self ke jagah **cls** hota hai

- **class variable**	  Sab objects ke liye ek hi value
- **cls**	              Class khud
- **@classmethod**	    Method jo class ke saath kaam kare


**@staticmethod**	    A method jo na class (cls) use karti hai, na object (self)


class MyCounter:
    count = 0

    @classmethod
    def show(cls):
        print(cls.count)   ✅ still works
       print(Counter.count) ❌ error (name doesn't exist anymore)


### Conclusion:
Counter.count likhna galat nahi hai

Lekin **cls.count** achhi practice hai because:

- Code reusable banta hai
- Class ka naam change ho toh code toot'ta nahi
- Inheritance ke case mein sahi class ke saath kaam karta hai

### Public variables aur methods 
- direct object ke through access ki ja sakti hain — koi restriction nahi hoti.

### 🤔 Why use static method?
- Jab aapko sirf logic run karna ho, bina object banaye
- Jaise calculator functions: add, multiply, sqrt, etc.

**Concept**	                **Explanation**
- Static Method	            No self, no cls
- Call style	           ClassName.method_name()
- Use case	                General-purpose helper functions

**Name mangling** is Python’s way of protecting private variables by changing their names internally.

- When you create a variable with double underscores like **__ssn**, Python mangles its name to something like:

**_Employee__ssn**
- So it cannot be accessed directly from outside the class.

### Name mangling only applies when:
- Variable name starts with two underscores __
- And does not end with two underscores (like __init__ is NOT mangled)

- Name mangling changes **__ssn** to **_ClassName__ssn** to make it harder to access from outside.


