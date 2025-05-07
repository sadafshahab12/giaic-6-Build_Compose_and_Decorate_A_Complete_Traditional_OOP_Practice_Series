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

### @price.setter def price(self, value):

- Ye setter method hai jo _price ki value update karta hai.
- Isme ek validation bhi hai: agar aap negative price set karte hain to error raise hota hai.

### @price.deleter def price(self):

- Ye deleter method hai jo _price attribute ko delete karta hai.
- Jab del product.price likha jata hai, to yeh method call hota hai aur price delete ho jata hai.

- Getter: Hum @property se kisi attribute ko easily access kar lete hain bina directly _price ko access kiye.

- Setter: Hum @property.setter se us attribute ko update karte hain.

- Deleter: Hum @property.deleter se attribute ko delete karte hain.


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

- ABC = Abstract Base Class
- @abstractmethod = Aisi function definition jo subclass ko likhni padegi
- 🔸 Humne Shape class banayi
- 🔸 Usme ek area() method rakha
- 🔸 area() ka body khali hai — matlab formula yaha nahi diya

### Shape	Abstract class — base idea
**Rectangle(Shape)**	    Child class — real implementation
**@abstractmethod**	        Forces area() to be defined in child
**super()?**	            Not used here — because we're not extending constructor logic

### super() ka matlab kya hota hai?
- super() ka use hum tab karte hain jab hum **parent (base)** class ka constructor ya method bhi chalana chahte hain **child (subclass)** ke constructor ke andar.


**Instance Variable**	    Belongs to one object (set inside __init__)
**Instance Method**	        Uses self to access instance variables

- self ka matlab: "yehi object" (jaise dog1)
- bark() is an instance method because it depends on the specific dog's name

**@classmethod** allows you to update or use class-level variables (like a counter). Use *cls* to refer to the class itself.

### Composition ka Matlab:
- Ek class ke andar doosri class ka object rakhna
- Jaise: Car has an Engine

**Feature**	        **is-a**	                            **has-a**
Type	            Inheritance (class B(A))	            Composition (A has B)
Meaning	            "B is an A"	                            "A has a B"
Example	            Dog is an Animal	                    Car has an Engine
Reusability	        Reuses behavior by inheriting	        Reuses by using other object

### 🧠 What is Aggregation?
Aggregation is a **“has-a”** relationship where:

- One class uses another,
- But both can exist separately.

📌 **Think:** A Department has Employees, but an Employee can exist without the Department too.

### MRO (Method Resolution Order) kya hai?
MRO ka matlab hai ki jab aap kisi object ka method call karte hain, to Python kis order mein us method ko search karega agar wo multiple classes se inherit ho raha ho

### Diamond Inheritance kya hota hai?
Diamond inheritance tab hota hai jab ek class do alag classes se inherit kar rahi ho, aur dono wo classes aik common class (base class) se inherit kar rahi ho.

### Aasaan Tareeqay Se Samajhna:
- Jab aap D ka object banate hain aur show() call karte hain, to Python pehle B ko dekhega, kyun ke D class pehle B se inherit karti hai.
- Agar B mein show() nahi hota, to C aur phir A ko check kiya jayega.
- Is tarah se, Python apni MRO list ke zariye decide karta hai ke kis class ka method pehle use ho.

### 🔹 Decorator Kya Hota Hai? (Asaan Alfaaz Mein)
Decorator ek function hota hai jo kisi doosray function ke **behavior ko change** karta hai bina us function ko **directly modify kiye**.

### @log_function_call: 
- Ye ek special syntax hai jo say_hello function par decorator apply karta hai.
- Jab bhi aap @log_function_call likhte hain, to Python internally say_hello ko log_function_call(say_hello) se replace kar deta hai.
 
### Class Decorator Kya Hota Hai?
- Class decorator ek aisi technique hai jisme hum ek class ko modify karte hain.
- Jab aap kisi class par decorator apply karte hain, to wo class ko alter (change) kar deta hai aur usmein kuch new functionality add kar sakta hai.

### Property Decorators:
- @property: Is decorator ko use karke hum kisi private attribute ko ek read-only property bana dete hain, jise hum directly access kar sakte hain.
- @property.setter: Ye decorator use karke hum property ki value ko update kar sakte hain.
- @property.deleter: Is decorator ko use karke hum property ko delete kar sakte hain.

### @property def price(self):

- Ye getter method hai jo _price ko return karta hai.
- Jab aap product.price likhte hain, to internally yeh @property decorator call hota hai, aur _price value return hoti hai.

### 🔹 __call__() method:
- Jab aap kisi object ko function ki tarah call karte hain (jaise obj()), to Python __call__() method ko call karta hai.

### 🔹 callable() function:
- Ye Python ka built-in function hai jo batata hai ke koi cheez (function, object, class) call ki ja sakti hai ya nahi.

- m = Multiplier(5)	m.factor = 5 set ho gaya
- callable(m)	True aayega, kyunki __call__() defined hai
- m(10)	Python actually m.__call__(10) run karta hai
- m(10) = 10 * 5 = 50	

### 🟢 Easy Samjhaana:
- __call__() likhne se object function ban jaata hai.
- callable() se check kar sakte hain ki object function ki tarah call ho sakta hai ya nahi.
  
### 🔹 class InvalidAgeError(Exception):
- Yahan hum Python ki built-in Exception class ko inherit karke apna custom error bana rahe hain.
- Ab jab bhi aapko specific error dikhani ho, aap ye custom error use kar sakte ho.

### ✅ self.start
- Yeh original starting value ko store karta hai.
- Isse aapko hamesha pata hota hai ke count kis number se shuru hua tha.

### ✅ self.current
- Yeh actual iteration ke liye use hota hai.
- Har __next__() call par ye decrease hota hai (self.current -= 1)
- Jab yeh 0 se neeche chala jata hai, tab StopIteration raise hota hai.


__iter__() ➜ Iterator banata hai
__next__() ➜ Next value return karta hai, aur jab khatam ho jaye to StopIteration deta hai
- __iter__	Returns self, kyunki yahi object iterate karega
- __next__	Har baar next value return karta hai, jab tak 0 tak na pahuch jaye
- StopIteration	Ye batata hai ke iteration khatam ho gaya

- self.current	For-loop ke liye counting karta hai (dynamic)




