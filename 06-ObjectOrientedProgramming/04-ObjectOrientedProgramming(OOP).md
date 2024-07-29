# Introduction to OOP in Python

**Object-Oriented Programming (OOP)** is a programming paradigm that uses the concept of "objects" to design and implement software systems. An object is a self-contained unit that encapsulates both data (attributes) and methods (functions) that operate on the data. This paradigm promotes a design approach where the focus is on objects rather than procedures or logic. 

In OOP, objects interact with one another through methods, providing a way to model real-world entities and their interactions. This paradigm is characterized by four primary principles: encapsulation, inheritance, abstraction, and polymorphism. By adhering to these principles, OOP helps developers create systems that are modular, reusable, and easier to maintain.

<img src="../_assets/oop_in_python.svg">

Today, OOP is a fundamental paradigm in software development, influencing many programming languages and methodologies. It has become an essential approach for designing scalable and maintainable systems.

## Importance of OOP for Data Engineers

Object-Oriented Programming is particularly significant for data engineers due to its impact on designing and managing data systems. Here’s how OOP benefits data engineers:

### Benefits for Data Modeling and Data Processing

1. **Modular Design**: OOP supports the creation of modular systems where data and behaviors are encapsulated within classes. This modularity is crucial for designing scalable data pipelines and systems where components can be developed, tested, and updated independently.
   
   *Example*: Consider a data pipeline for processing user activity logs. Using OOP, you can design classes such as `LogReader`, `DataCleaner`, and `DataWriter`. Each class handles a specific part of the pipeline, making it easier to modify or replace components without disrupting the entire system.

2. **Reusability**: OOP promotes code reusability through inheritance and polymorphism. Common functionalities can be abstracted into base classes and reused across different parts of your data processing system, reducing redundancy and improving maintainability.
   
   *Example*: A base class `DataProcessor` might include generic methods for data processing, such as `load_data` and `save_data`. Concrete subclasses like `CSVProcessor` and `JSONProcessor` can inherit from `DataProcessor` and implement specific details for handling CSV and JSON formats, respectively.

3. **Encapsulation**: Encapsulation allows for bundling data and related methods into a single unit, protecting the internal state of objects and reducing complexity. This helps in maintaining data integrity and simplifies the management of complex systems.
   
   *Example*: In a class `DatabaseConnection`, encapsulate methods for connecting to and interacting with a database, such as `connect` and `query`. By hiding the internal implementation details, you ensure that changes to connection logic do not impact other parts of your application.

4. **Abstraction**: OOP provides abstraction by enabling you to focus on high-level functionalities while hiding low-level implementation details. This is particularly useful for managing complex data structures and algorithms.
   
   *Example*: An abstract class `DataTransformer` may define methods like `transform`, while concrete subclasses like `NormalizationTransformer` or `ScalingTransformer` provide specific implementations. This allows for working with various transformations at a higher level of abstraction.

5. **Maintainability and Extensibility**: OOP makes it easier to maintain and extend codebases. Well-designed object-oriented systems are flexible and can be extended with new features or modifications with minimal disruption to existing code.
   
   *Example*: Adding a new feature, such as a logging mechanism, can be accomplished by creating a new class `Logger` and integrating it into existing classes. This approach minimizes the impact on existing functionality and supports smooth evolution of the system.

### Real-world Applications in Data Engineering

1. **Data Pipelines**: OOP facilitates the design of complex data pipelines, with each stage of processing represented as an object. This approach enhances the clarity and manageability of data processing workflows.
   
   *Example*: In a data ingestion pipeline, you might design classes such as `DataExtractor`, `DataTransformer`, and `DataLoader`. Each class manages a specific aspect of the pipeline, providing a clear structure for the overall process.

2. **Data Models**: OOP helps in creating clear and maintainable data models that reflect real-world entities and their relationships. This approach simplifies the representation and management of complex data structures.
   
   *Example*: For an e-commerce application, data models might include classes like `Customer`, `Order`, and `Product`. Each class encapsulates attributes and methods relevant to its respective entity, providing a coherent model of the system.

3. **Configuration Management**: OOP is useful for managing configuration settings across different environments (e.g., development, testing, production). Configuration objects can encapsulate settings and provide methods for accessing and modifying them.
   
   *Example*: A `ConfigManager` class can manage configuration settings, such as database connections and API keys, offering a unified interface for handling these settings across various parts of the application.

# Python Classes and Objects

In this section, we'll cover the basics of Python classes and objects, focusing on how to define and use them. By the end of this section, you'll understand how to create simple classes, instantiate objects, and interact with them.

## What is a Class?

A **class** is a blueprint for creating objects. It encapsulates data for the object and methods to operate on that data. Think of a class as a template that describes the properties and behaviors that the objects created from it will have.

### Defining a Class

To define a class in Python, use the `class` keyword followed by the class name (by convention, class names use **CamelCase**). Inside the class definition, you can define attributes (data) and methods (functions) that operate on the data.

**Example:**

```python
class Car:
    # The constructor method (initializer)
    def __init__(self, make, model, year):
        self.make = make  # Attribute for make
        self.model = model  # Attribute for model
        self.year = year  # Attribute for year

    # Method to display car information
    def display_info(self):
        return f"{self.year} {self.make} {self.model}"
```

- **`__init__` Method**: This is the **constructor** or initializer method, which is called when a new object is created. It initializes the object's attributes.
- **`self` Parameter**: Refers to the instance of the class. It allows access to the instance’s attributes and methods.

### Creating and Using Objects

An **object** is an instance of a class. Once a class is defined, you can create objects from it by calling the class name as if it were a function.

**Example:**

```python
# Creating an object of the Car class
my_car = Car("Toyota", "Corolla", 2022)

# Using the object's method
print(my_car.display_info())
```

**Output:**

```
2022 Toyota Corolla
```

## Attributes and Methods

### Instance Attributes

Instance attributes are specific to each object created from the class. They are defined within the `__init__` method using the `self` keyword.

**Example:**

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        return f"{self.name} says Woof!"
```

Creating an Object and Accessing Attributes:

```python
# Creating an object of the Dog class
my_dog = Dog("Buddy", 4)

# Accessing attributes
print(f"{my_dog.name} is {my_dog.age} years old.")

# Calling a method
print(my_dog.bark())
```

**Output:**

```
Buddy is 4 years old.
Buddy says Woof!
```

### Instance Methods

Instance methods are functions defined inside the class that operate on the instance's data. They always take `self` as the first parameter.

**Example:**

```python
class Circle:
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        import math
        return math.pi * (self.radius ** 2)

    def circumference(self):
        import math
        return 2 * math.pi * self.radius
```

Creating an Object and Using Methods:

```python
# Creating an object of the Circle class
my_circle = Circle(5)

# Using methods
print(f"Area: {my_circle.area():.2f}")
print(f"Circumference: {my_circle.circumference():.2f}")
```

**Output:**

```
Area: 78.54
Circumference: 31.42
```

## Class Attributes and Methods

### Class Attributes

Class attributes are shared among **all instances of a class**. They are defined directly within the class, but outside any methods.

**Example:**

```python
class Student:
    school_name = "Springfield High"  # Class attribute

    def __init__(self, name, grade):
        self.name = name
        self.grade = grade

    def display_info(self):
        return f"{self.name} is in grade {self.grade} at {Student.school_name}"
```

Using Class Attributes:

```python
# Creating objects of the Student class
student1 = Student("Alice", 10)
student2 = Student("Bob", 12)

# Accessing class attribute through objects
print(student1.display_info())
print(student2.display_info())

# Accessing class attribute directly from the class
print(Student.school_name)
```

**Output:**

```
Alice is in grade 10 at Springfield High
Bob is in grade 12 at Springfield High
Springfield High
```

### Class Methods

Class methods operate on class attributes rather than instance attributes. They are defined with the `@classmethod` decorator and take `cls` as the first parameter.

**Example:**

```python
class Counter:
    count = 0  # Class attribute

    def __init__(self):
        Counter.count += 1

    @classmethod
    def get_count(cls):
        return cls.count
```

Using Class Methods:

```python
# Creating objects
counter1 = Counter()
counter2 = Counter()

# Calling class method
print(Counter.get_count())  # Output: 2
```

# Object-Oriented Programming Principles in Python

Object-Oriented Programming (OOP) is a paradigm centered around the concept of "objects," which bundle data and behavior together into single units known as classes. Key principles of OOP include **encapsulation**, **inheritance**, **abstraction**, and **polymorphism**. Encapsulation involves bundling data and methods into classes and protecting the internal state of objects from external interference. Inheritance allows new classes to inherit attributes and methods from existing classes, promoting code reuse and creating hierarchical relationships. Abstraction simplifies complex systems by focusing on essential characteristics and hiding unnecessary details, while polymorphism enables different classes to be treated through a common interface, allowing for flexible and dynamic code.

These OOP principles collectively support a modular and organized approach to software design, making it easier to manage complexity, enhance code reusability, and create maintainable systems. By adhering to these principles, developers can build robust applications that are not only easier to understand and extend but also more adaptable to changing requirements. Understanding and applying these concepts effectively is essential for leveraging the full potential of object-oriented programming in Python and other languages.

## 1. Encapsulation

Encapsulation is a fundamental principle of object-oriented programming that is pivotal for designing robust and maintainable software. It refers to the practice of bundling data (attributes) and methods (functions) that operate on that data into a single unit or class. This principle not only helps in organizing code but also protects the internal state of an object from unintended modifications.

Encapsulation in Python involves creating classes to encapsulate data and functionality. By defining attributes and methods within a class, you create a blueprint for objects. These objects manage their own state and expose only the necessary methods to interact with that state.

**Example:**

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Private attribute

    def deposit(self, amount):
        self.__balance += amount

    def withdraw(self, amount):
        if amount <= self.__balance:
            self.__balance -= amount
        else:
            print("Insufficient funds!")

    def get_balance(self):
        return self.__balance
```

**Using Encapsulation:**

```python
account = BankAccount(1000)
account.deposit(500)
print(account.get_balance())  # Output: 1500
account.withdraw(200)
print(account.get_balance())  # Output: 1300
```

Encapsulation involves restricting direct access to some of the object's components and only exposing a controlled interface. This is done using **private attributes and methods**.

### Private Attributes and Methods

In Python, the concept of private attributes and methods is an important part of encapsulation. While Python does not enforce strict access control like some other languages (such as Java or C++), it provides naming conventions that help indicate the intended visibility of class members (attributes and methods). Here's an in-depth explanation of private attributes and methods in Python:

#### 1. Naming Conventions for Privacy

In Python, privacy is not enforced by the language itself but is instead guided by naming conventions:

**Single Underscore (`_`)**: A single underscore at the beginning of a variable or method name is a convention to indicate that it is intended for internal use (**protected**). It signals that this member is protected and should not be accessed from outside the class. However, it does not prevent access; it's more of a guideline for developers.

```python
class Example:
    def __init__(self):
        self._protected_attribute = "This is protected"
```

**Double Underscore (`__`)**: A double underscore prefix makes the name of the attribute or method more "**private**" by triggering name mangling. This means that Python changes the name of the attribute or method in a way that makes it harder (but not impossible) to access from outside the class.

```python
class Example:
    def __init__(self):
        self.__private_attribute = "This is private"

    def __private_method(self):
        return "This is a private method"

    def public_method(self):
        return self.__private_method()
```

In the example above, `__private_attribute` and `__private_method` are subjected to name mangling, which changes their names internally to include the class name, making them less accessible from outside the class.

**Accessing Mangled Names**:

```python
example = Example()
print(example._Example__private_attribute)  # This will work, but it's not recommended
```

#### 2. Why Use Private Attributes and Methods?

- **Data Protection**: By using private attributes and methods, you can protect the internal state of an object from unintended or unauthorized modifications. This helps maintain data integrity and ensures that the class's internal logic is not inadvertently broken by external code.

- **Encapsulation**: Private attributes and methods help encapsulate the internal workings of a class. This encapsulation hides the implementation details from the user of the class and exposes only the necessary interface. This makes the code more modular and easier to maintain.

- **Implementation Hiding**: Private members allow you to change the internal implementation of a class without affecting code that depends on the public interface. This is particularly useful for refactoring and evolving code.

#### 3. Example Usage

Here’s a detailed example to illustrate the use of private attributes and methods:

```python
class BankAccount:
    def __init__(self, account_number, balance):
        self.__account_number = account_number
        self.__balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
        else:
            print("Deposit amount must be positive.")

    def withdraw(self, amount):
        if 0 < amount <= self.__balance:
            self.__balance -= amount
        else:
            print("Invalid withdrawal amount.")

    def get_balance(self):
        return self.__balance

    def __generate_account_summary(self):
        return f"Account Number: {self.__account_number}, Balance: {self.__balance}"

    def show_summary(self):
        print(self.__generate_account_summary())

# Usage
account = BankAccount("12345678", 1000)
account.deposit(500)
account.withdraw(200)
print(account.get_balance())  # Output: 1300

# The following will raise an error or is not recommended
# print(account.__generate_account_summary())  # AttributeError
# print(account.__account_number)  # AttributeError

# The public method can still access the private method
account.show_summary()  # Output: Account Number: 12345678, Balance: 1300
```

In this example:

- `__account_number` and `__balance` are private attributes that should not be accessed directly from outside the class.
- `__generate_account_summary` is a private method used internally within the class.
- `show_summary` is a public method that provides controlled access to the private summary functionality.

#### 4. Challenges and Considerations

- **Access Flexibility**: Python's approach to private members is more about conventions and less about enforcement. While name mangling adds a layer of obfuscation, it doesn’t provide true security. Determined users can still access private members if they know how.

- **Overuse**: Overusing private members can lead to overly rigid designs. It’s essential to balance privacy with flexibility, making sure that the public interface remains usable and that internal details are appropriately abstracted.

- **Documentation**: Clear documentation is crucial. Even though some attributes or methods are private, understanding their purpose and usage through documentation helps maintain and extend the code effectively.

#### Public, Protected, and Private Attributes

| **Access Modifier** | **Description**                                                                                                                                           | **Syntax**                      | **Use Cases**                                                                                                                                                                          | **Example**                                                                                                                                          |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Public**          | Members are accessible from anywhere in the code. They are part of the class's public API.                                                                | No prefix                       | - Define public methods and attributes that should be accessible from outside the class. <br> - Methods that interact with other components of the application.                        | ```python class MyClass: <br> def __init__(self): <br> self.value = 10 <br> def get_value(self): <br> return self.value <br> ```                     |
| **Protected**       | Members are intended to be used only within the class and its subclasses. The single underscore is a convention and does not enforce access restrictions. | Single underscore prefix (`_`)  | - Use when you want to indicate that a member is part of the internal implementation but might be needed by subclasses. <br> - Internal APIs that subclasses might override or extend. | ```python class MyBaseClass: <br> def __init__(self): <br> self._internal_value = 5 <br> def _internal_method(self): <br> return "Internal" <br> ``` |
| **Private**         | Members are intended to be used only within the class. Name mangling is used to make the attribute harder to access from outside.                         | Double underscore prefix (`__`) | - Use when you want to hide internal details of the class that should not be accessed or modified from outside. <br> - To prevent accidental modification of internal state.           | ```python class MyClass: <br> def __init__(self): <br> self.__private_value = 20 <br> def __private_method(self): <br> return "Private" <br> ```     |

<p style="text-align: center">
<img title="" src="../_assets/access_modifire.svg" alt="access modifire" style="zoom: 40%;" data-align="center">
</p>

##### Public Members

Public members are accessible from any part of the code. They are the standard way to expose functionality or data from a class.

- **Use Cases**: 
  - Methods that provide the main functionality of the class.
  - Attributes that need to be accessed or modified by other classes or modules.
  - Parts of the class API that are intended for general use.

##### Protected Members

Protected members are intended to be used within the class and its subclasses. The single underscore is a convention that suggests that these members are not part of the public API.

- **Use Cases**:
  - Methods and attributes that should be accessible to subclasses but not to external code.
  - Internal functionality that may need to be extended or customized by subclasses.
  - Intermediate level of encapsulation where the members are somewhat exposed but not meant to be part of the class’s public API.

##### Private Members

**Description**: Private members are meant to be accessible only within the class. The double underscore prefix triggers name mangling, which makes it harder (but not impossible) to access these members from outside the class.

- **Use Cases**:
  - To hide internal details that should not be accessed or modified from outside.
  - When you need to ensure that the internal state of the class is protected from external interference.
  - To encapsulate data and behavior strictly within the class, preventing accidental usage or modification.

### Encapsulation in Data Pipelines

Applying encapsulation in data pipelines can help manage complexity, improve data integrity, and make your code more modular and reusable. Here’s how encapsulation can be effectively used in data pipelines:

#### 1. Modular Design of Data Processing Components

Encapsulation allows you to design data processing components as distinct classes with their own data and methods. This means each component can manage its own state and operations, hiding the internal details from other parts of the pipeline.

**Example:**

- **Data Ingestion Module:** Encapsulate logic for reading data from various sources (e.g., databases, APIs, files) in a class. This class can have methods to connect to the data source, read data, and handle errors, while hiding the implementation details from the rest of the pipeline.
- **Data Transformation Module:** Create a class to encapsulate data transformation logic, such as cleaning, aggregating, or enriching data. This class can have methods for applying specific transformations, and it maintains its own state regarding the transformation rules.

**Benefits:**

- **Isolation:** Changes to the internal workings of one module do not affect others.
- **Reusability:** Encapsulated components can be reused across different pipelines or projects.

#### 2. Data Validation and Error Handling

Encapsulation helps in managing data validation and error handling by grouping these responsibilities within dedicated classes. This ensures that data validation rules and error handling mechanisms are consistent and maintainable.

**Example:**

- **Data Validator Class:** Encapsulate data validation logic within a class that includes methods for checking data quality, consistency, and format. The pipeline components can use this class to validate data before further processing.
- **Error Handler Class:** Design a class responsible for logging and managing errors that occur during the pipeline execution. This class can provide methods for recording errors, notifying stakeholders, or retrying failed operations.

**Benefits:**

- **Centralized Error Management:** All error handling logic is contained within one class, making it easier to maintain and update.
- **Consistency:** Ensures that validation and error handling are uniformly applied across the pipeline.

#### 3. Encapsulation of Configuration Settings

Configuration settings for data pipelines, such as file paths, database credentials, and processing parameters, can be encapsulated within a configuration class. This approach keeps configuration details separate from business logic.

**Example:**

- **Configuration Class:** Create a class to manage configuration settings, including methods to load settings from environment variables, configuration files, or other sources. This class can provide access to configuration values in a controlled manner.

**Benefits:**

- **Separation of Concerns:** Keeps configuration management separate from data processing logic.
- **Flexibility:** Allows for easy updates to configuration settings without modifying the core pipeline logic.

#### Example: Encapsulation in Data Pipeline

Here’s a simplified example demonstrating encapsulation in a data pipeline:

```python
# Data Ingestion Module
class DataIngestion:
    def __init__(self, source):
        self._source = source  # Protected attribute

    def connect(self):
        # Logic to connect to the data source
        pass

    def fetch_data(self):
        # Logic to fetch data from the source
        pass

# Data Transformation Module
class DataTransformation:
    def __init__(self):
        self._data = None  # Protected attribute

    def load_data(self, data):
        self._data = data

    def transform(self):
        # Logic to transform data
        pass

# Data Validator Module
class DataValidator:
    def validate(self, data):
        # Logic to validate data
        pass

# Data Pipeline
class DataPipeline:
    def __init__(self, source):
        self.ingestion = DataIngestion(source)
        self.transformation = DataTransformation()
        self.validator = DataValidator()

    def run(self):
        self.ingestion.connect()
        data = self.ingestion.fetch_data()
        if self.validator.validate(data):
            self.transformation.load_data(data)
            self.transformation.transform()
            # Further processing

# Example usage
pipeline = DataPipeline('data_source')
pipeline.run()
```

In this example:

- **`DataIngestion`, `DataTransformation`, and `DataValidator`** classes encapsulate their respective responsibilities.
- **`DataPipeline`** class coordinates the interaction between these encapsulated components, providing a clear and modular structure.

#### Challenges of Encapsulation in Data Pipelines

1. **Overhead of Class Design:** Encapsulation requires careful design of classes and methods, which can introduce overhead in terms of initial development time and complexity.
2. **Balancing Encapsulation and Performance:** Excessive encapsulation may lead to performance overhead due to increased method calls and data handling. It's important to balance encapsulation with performance considerations.
3. **Managing Dependencies:** Encapsulated components may have dependencies that need to be managed, which can add complexity to the pipeline setup and configuration.

### Properties in Python

Properties provide a way to manage attribute access and modification with more control. The `property` decorator allows you to define methods that are accessed like attributes.

In Python, the `property` decorator is a built-in feature that allows you to define methods in a class that act like attributes. This provides a way to manage the access and modification of an object's attributes in a controlled manner, adding a layer of abstraction while keeping the code clean and readable.

#### The `property` Decorator

The `property` decorator allows you to define methods that are accessed like attributes. This means you can control how attributes are retrieved, set, and deleted while presenting a clean and intuitive interface for users of your class. 

##### How It Works

1. **Basic Structure:**
   
   The `property` decorator is used to define **getter, setter, and deleter** **methods** for a property in a class.
   
   ```python
   class MyClass:
       def __init__(self, value):
           self._value = value  # Private attribute
   
       @property
       def value(self):
           return self._value  # Getter method
   
       @value.setter
       def value(self, new_value):
           if new_value > 0:
               self._value = new_value  # Setter method
           else:
               raise ValueError("Value must be positive")
   
       @value.deleter
       def value(self):
           del self._value  # Deleter method
   ```

2. **Using the Property:**
   
   ```python
   obj = MyClass(10)
   print(obj.value)  # Calls the getter method
   obj.value = 20    # Calls the setter method
   del obj.value     # Calls the deleter method
   ```

##### Components of the `property` Decorator

1. **Getter Method:**
   
   The method decorated with `@property` is known as the **getter**. It is called when the property is accessed.
   
   ```python
   @property
   def value(self):
       return self._value
   ```

2. **Setter Method:**
   
   The method decorated with `@property_name.setter` is the setter. It is called when the property is assigned a new value.
   
   ```python
   @value.setter
   def value(self, new_value):
       if new_value > 0:
           self._value = new_value
       else:
           raise ValueError("Value must be positive")
   ```

3. **Deleter Method:**
   
   The method decorated with `@property_name.deleter` is the deleter. It is called when the property is deleted.
   
   ```python
   @value.deleter
   def value(self):
       del self._value
   ```

##### Use Cases and Applications

1. **Controlled Access to Private Attributes:**
   
   The `property` decorator allows you to control how private attributes are accessed and modified. This encapsulation ensures that attributes are manipulated in a controlled manner, adding validation and logic as needed.
   
   ```python
   class Person:
       def __init__(self, name):
           self._name = name
   
       @property
       def name(self):
           return self._name
   
       @name.setter
       def name(self, value):
           if isinstance(value, str) and value:
               self._name = value
           else:
               raise ValueError("Name must be a non-empty string")
   ```

2. **Computed Properties:**
   
   Properties can be used to create attributes whose values are computed dynamically based on other attributes. This allows you to present a clean interface while managing complex calculations internally.
   
   ```python
   class Rectangle:
       def __init__(self, width, height):
           self._width = width
           self._height = height
   
       @property
       def area(self):
           return self._width * self._height
   ```

3. **Read-Only Properties:**
   
   You can create properties that are read-only by defining only the getter method and omitting the setter method. This is useful for attributes that should not be modified after initialization.
   
   ```python
   class Circle:
       def __init__(self, radius):
           self._radius = radius
   
       @property
       def radius(self):
           return self._radius
   
       @property
       def diameter(self):
           return self._radius * 2
   ```

##### Challenges and Considerations

1. **Readability and Maintenance:**
   
   While properties enhance encapsulation, overusing them can lead to code that is harder to read and maintain. It’s important to use properties judiciously and ensure that they add value to the code.

2. **Performance Overheads:**
   
   Properties introduce method calls for attribute access, which might have performance implications if not used carefully. For performance-critical applications, assess whether the use of properties is appropriate.

3. **Complexity:**
   
   Adding logic to getters, setters, and deleters can increase the complexity of the class. Ensure that the added complexity provides a clear benefit, such as validation or computed values.

The `property` decorator in Python is a powerful feature for managing access to attributes in a controlled and intuitive manner. By using properties, you can ***encapsulate logic***, ***validate data***, and manage ***attribute access and modification*** while presenting a clean and user-friendly interface. Understanding how to effectively use properties is essential for writing maintainable and robust Python code.

### Encapsulation in Python's Data Structures

Python’s built-in data types and custom data structures offer practical examples of encapsulation. This tutorial explores how encapsulation is implemented in Python’s built-in types and how to design custom data structures with encapsulation.

Python’s built-in data types, such as lists, dictionaries, and sets, provide encapsulation by abstracting the complexity of data management. Here's how encapsulation manifests in these types:

#### Lists

Python lists encapsulate data by providing methods to access, modify, and manage elements. Operations such as appending, removing, or sorting elements are handled by the list’s internal implementation, abstracting away the details from the user.

**Example:**

```python
my_list = [1, 2, 3]
my_list.append(4)  # Encapsulation: appends to the internal list without exposing its implementation
print(my_list)     # Output: [1, 2, 3, 4]
```

**Limitations:**

Lists are dynamically sized and handle various operations internally. While this provides ease of use, it can sometimes obscure how these operations affect performance and memory usage.

#### Dictionaries

Dictionaries encapsulate data through key-value pairs, allowing efficient data retrieval and modification. Methods like `get`, `update`, and `pop` manage the dictionary’s internal state.

**Example:**

```python
my_dict = {'a': 1, 'b': 2}
my_dict.update({'c': 3})  # Encapsulation: updates the internal dictionary without exposing its structure
print(my_dict)           # Output: {'a': 1, 'b': 2, 'c': 3}
```

**Limitations:**

Dictionaries manage internal hashing and resizing, which can lead to performance overhead. Users must rely on the dictionary’s methods and cannot directly manipulate the underlying data structure.

#### Sets

Sets encapsulate data by managing unique elements. Methods like `add`, `remove`, and `discard` handle internal data management while providing a simple interface to users.

**Example:**

```python
my_set = {1, 2, 3}
my_set.add(4)          # Encapsulation: adds to the internal set without exposing its implementation
print(my_set)         # Output: {1, 2, 3, 4}
```

**Limitations:**

Sets handle internal hashing and maintain uniqueness, which may not be apparent to users. The details of how collisions and resizing are managed are abstracted away.

### Custom Data Structures with Encapsulation

Designing custom data structures involves creating classes that encapsulate data and provide methods to interact with that data. Here are examples of encapsulating behavior in stacks, queues, and linked lists.

#### 1. Stacks

A stack is a data structure that follows the **Last In, First Out (LIFO)** principle. Encapsulation in a stack involves hiding the internal list and providing methods to push and pop elements.

```python
class Stack:
    def __init__(self):
        self._items = []  # Internal list to store stack elements

    def push(self, item):
        self._items.append(item)  # Encapsulates the action of adding an item

    def pop(self):
        if not self.is_empty():
            return self._items.pop()  # Encapsulates the action of removing an item
        raise IndexError("Pop from empty stack")

    def is_empty(self):
        return len(self._items) == 0  # Encapsulation: hides the details of stack size

    def peek(self):
        if not self.is_empty():
            return self._items[-1]  # Encapsulation: retrieves the top item without removing it
        raise IndexError("Peek from empty stack")
```

**Use Case:**

- Stacks are useful in algorithms requiring backtracking, such as depth-first search or undo operations in applications.

#### 2. Queues

A queue is a data structure that follows the First In, First Out (FIFO) principle. Encapsulation in a queue involves managing the internal list and providing methods to enqueue and dequeue elements.

```python
class Queue:
    def __init__(self):
        self._items = []  # Internal list to store queue elements

    def enqueue(self, item):
        self._items.append(item)  # Encapsulates the action of adding an item

    def dequeue(self):
        if not self.is_empty():
            return self._items.pop(0)  # Encapsulates the action of removing an item
        raise IndexError("Dequeue from empty queue")

    def is_empty(self):
        return len(self._items) == 0  # Encapsulation: hides the details of queue size
```

**Use Case:**

- Queues are commonly used in task scheduling, breadth-first search algorithms, and buffering.

#### 3. Linked Lists

A linked list is a data structure consisting of nodes, where each node points to the next node in the sequence. Encapsulation involves managing the nodes and providing methods to add, remove, and traverse nodes.

```python
class Node:
    def __init__(self, data):
        self.data = data  # Data stored in the node
        self.next = None  # Pointer to the next node

class LinkedList:
    def __init__(self):
        self.head = None  # Head node of the list

    def append(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node  # Encapsulation: sets the head node if the list is empty
        else:
            current = self.head
            while current.next:
                current = current.next
            current.next = new_node  # Encapsulation: adds a new node to the end of the list

    def display(self):
        current = self.head
        while current:
            print(current.data, end=' -> ')
            current = current.next
        print("None")  # Encapsulation: displays the list elements
```

**Use Case:**

- Linked lists are useful for scenarios where frequent insertions and deletions are required, such as implementing dynamic data structures and managing memory efficiently.

Encapsulation in Python's built-in data types and custom data structures provides a powerful mechanism to abstract complexity and manage data effectively. Understanding how to leverage encapsulation helps in designing robust and maintainable code, especially in complex systems. Whether using Python’s built-in types or creating custom structures, encapsulation ensures that data is protected and managed through well-defined interfaces.

### Encapsulation and Performance

While encapsulation provides many benefits in terms of code maintainability and abstraction, it can also impact performance. Understanding these impacts and learning how to optimize performance while maintaining good encapsulation practices is essential for efficient and effective programming

#### Performance Considerations

Encapsulation affects performance in various ways, primarily by influencing code execution and resource management. Below, we discuss the performance impact of encapsulation and strategies for optimizing it.

##### 1. Evaluating the Performance Impact

Encapsulation introduces some overhead due to the additional layers of abstraction and method calls. However, this impact is often minimal compared to the benefits of code clarity and maintainability. Performance considerations include:

- **Method Call Overhead:**
  
  Every method call involves some overhead, which may add up in performance-critical sections of the code. While individual method calls are usually fast, excessive method calls or deeply nested method invocations can impact performance.

- **Data Access Patterns:**
  
  Encapsulation often involves accessor methods (getters and setters) that control data access. Frequent use of these methods instead of direct attribute access can introduce slight performance penalties. 

- **Complexity of Internal State Management:**
  
  Encapsulation can sometimes lead to more complex internal state management, especially if the class maintains multiple internal attributes and invariants. This added complexity can affect performance if not managed carefully.

**Example:**

Consider a class with a simple method that computes the square of a number:

```python
class Calculator:
    def __init__(self):
        self._value = 0

    def set_value(self, value):
        self._value = value

    def square(self):
        return self._value * self._value
```

In performance-critical applications, you might measure the impact of encapsulation by comparing this approach with direct attribute access:

```python
class CalculatorDirect:
    def __init__(self):
        self.value = 0

    def square(self):
        return self.value * self.value
```

##### 2. Strategies for Optimizing Performance

To optimize performance while maintaining good encapsulation practices, consider the following strategies:

- **Minimize Method Calls:**
  
  Avoid unnecessary method calls and aim for efficiency in accessor methods. For instance, if a method performs complex operations, ensure it’s well-optimized.

- **Use Efficient Data Structures:**
  
  Choose data structures that are appropriate for your needs and avoid excessive overhead. For example, using a `list` instead of a `set` when order matters but uniqueness does not.

- **Profile and Benchmark:**
  
  Use profiling tools to identify performance bottlenecks in your encapsulated code. Python’s built-in `cProfile` module or third-party tools like `line_profiler` can help analyze and optimize performance.

#### Memory Management

Encapsulation impacts memory usage and management due to the way objects are created, managed, and destroyed in Python. Understanding these impacts helps in optimizing memory consumption.

##### 1. How Encapsulation Affects Memory Usage

- **Object Overhead:**
  
  Each instance of a class has a memory overhead, including space for the object itself and for each attribute. Encapsulation adds a small amount of additional memory usage due to the need to store methods and internal state.

- **Internal State Management:**
  
  Encapsulation often involves storing internal state within objects. Proper management of this state is crucial, as excessive or inefficient use of attributes can lead to increased memory consumption.

- **Garbage Collection:**
  
  Python’s garbage collector automatically manages memory, but objects that are encapsulated and referenced by other objects may impact garbage collection performance. Circular references and large numbers of objects can complicate memory management.

**Example:**

Consider the following class with multiple attributes:

```python
class Person:
    def __init__(self, name, age):
        self._name = name
        self._age = age
```

While this class is straightforward, each instance consumes memory for the attributes `_name` and `_age`. In large-scale applications, efficient use of attributes and careful design can help minimize memory overhead.

##### 2. Techniques for Minimizing Memory Overhead

- **Optimize Attribute Storage:**
  
  Use attributes judiciously and avoid storing unnecessary data. For example, if an attribute can be computed on demand, consider using a method or property instead of storing it directly.

- **Use `__slots__`:**
  
  Python provides the `__slots__` mechanism to limit the attributes an object can have. This reduces memory overhead by preventing the creation of a dynamic `__dict__` for each object.
  
  ```python
  class Person:
      __slots__ = ['name', 'age']
  
      def __init__(self, name, age):
          self.name = name
          self.age = age
  ```

- **Manage Object Lifetimes:**
  
  Ensure objects are properly managed and cleaned up when no longer needed. Avoid creating long-lived references to objects that can be garbage collected.

- **Avoid Circular References:**
  
  Be mindful of circular references, as they can complicate garbage collection and lead to memory leaks. Use weak references if necessary to avoid these issues.

---

## 2. Inheritance

Inheritance is a fundamental concept in object-oriented programming (OOP) that allows one class to inherit attributes and methods from another class. This mechanism promotes code reuse and establishes a hierarchical relationship between classes.

### What is Inheritance?

Inheritance allows a new class (child or subclass) to inherit the characteristics (attributes and methods) of an existing class (parent or superclass). This concept helps in reusing code and establishing a natural hierarchy between classes.

### Basic Syntax

In Python, inheritance is implemented by defining a new class that inherits from an existing class. The syntax is straightforward:

```python
class ParentClass:
    def __init__(self, value):
        self.value = value

    def show(self):
        print(f"Value: {self.value}")

class ChildClass(ParentClass):
    def __init__(self, value, extra):
        super().__init__(value)
        self.extra = extra

    def display(self):
        print(f"Extra: {self.extra}")
```

In this example:

- `ParentClass` is the parent class with an `__init__` method and a `show` method.
- `ChildClass` inherits from `ParentClass` and has its own `__init__` and `display` methods.

<img title="" src="../_assets/iinheritance_in_python.svg" alt="inheritance in python" data-align="center">

### Accessing Parent Class Methods

In Python, the `super()` function is a powerful tool used to call methods from a parent class. It provides a way to access and invoke methods that are defined in the parent class from within the child class, and is crucial for maintaining a well-structured inheritance hierarchy. Understanding how to use `super()` effectively is important for implementing clean, maintainable, and extensible object-oriented code.

The `super()` function returns a temporary object of the superclass that allows access to its methods. This function is used in the context of class methods, particularly the `__init__` method, to ensure that the parent class is properly initialized and to call methods defined in the parent class.

**Syntax:**

```python
super().method_name()
```

Where `method_name` is the name of the method you want to call from the parent class.

#### Basic Usage of `super()`

The most common use of `super()` is in the `__init__` method of a subclass to initialize its parent class:

```python
class Parent:
    def __init__(self, name):
        self.name = name

    def greet(self):
        print(f"Hello from Parent, {self.name}")

class Child(Parent):
    def __init__(self, name, age):
        super().__init__(name)  # Calling the parent class's __init__ method
        self.age = age

    def introduce(self):
        super().greet()  # Calling the parent class's greet method
        print(f"I am {self.age} years old")

child = Child("Alice", 10)
child.introduce()
# Output:
# Hello from Parent, Alice
# I am 10 years old
```

In this example:

- `super().__init__(name)` initializes the `Parent` class with the `name` attribute.
- `super().greet()` calls the `greet` method from the `Parent` class within the `introduce` method of the `Child` class.

#### Common Pitfalls with `super()`

1. **Forgetting to Call `super()`**: In some cases, failing to call `super()` can lead to issues, especially if the parent class requires initialization.
2. **Incorrect MRO**: In complex inheritance hierarchies, understanding the MRO is essential to ensure that `super()` calls are resolved correctly.
3. **Compatibility with Old-Style Classes**: While Python 3 supports new-style classes, `super()` does not work with old-style classes, so ensure your classes are using Python 3's new-style classes.

### Multiple Inheritance in Python

**Multiple inheritance** is a feature in object-oriented programming where a class can inherit attributes and methods from more than one parent class. This allows a class to combine functionalities from multiple sources, promoting code reuse and flexibility. Python supports multiple inheritance, and understanding how it works is crucial for designing complex class hierarchies.

In multiple inheritance, a derived class inherits from two or more base classes. This allows the derived class to access and use the attributes and methods from all its parent classes.

**Example:**

```python
class Base1:
    def method1(self):
        print("Method from Base1")

class Base2:
    def method2(self):
        print("Method from Base2")

class Derived(Base1, Base2):
    def method3(self):
        print("Method from Derived")

d = Derived()
d.method1()  # Inherited from Base1
d.method2()  # Inherited from Base2
d.method3()  # Defined in Derived
```

In this example:

- `Derived` class inherits from both `Base1` and `Base2`.
- It has access to methods from both base classes and can also define its own methods.

<img title="" src="../_assets/mult_inheritance.svg" alt="multi inheritance" data-align="center">

#### Method Resolution Order (MRO)

**Method Resolution Order (MRO)** is a mechanism used by Python to determine the order in which base classes are searched when calling a method or accessing an attribute in a class hierarchy. This mechanism becomes particularly important in multiple inheritance scenarios to resolve ambiguities and ensure a consistent method lookup process.

The MRO specifies the order in which classes are considered when searching for a method or attribute. Python uses the **C3 linearization algorithm** to compute this order, which provides a consistent and predictable way to handle method lookups in complex class hierarchies.

**Key Points:**

- **Linearization**: MRO linearizes the class hierarchy into a single list that reflects the order in which classes are searched.
- **Consistency**: Ensures that each class appears in the MRO list only once and follows a consistent order of resolution.
- **Algorithm**: The C3 linearization algorithm is used to compute the MRO, which takes into account the order of base classes and the hierarchy in which they are defined.

##### C3 Linearization Algorithm

The C3 linearization algorithm determines the MRO by merging the MROs of the parent classes with the order in which they are listed. The algorithm is designed to provide a consistent order while respecting the inheritance hierarchy and avoiding ambiguities.

**Steps in C3 Linearization:**

1. **Create a list**: Start with the list of the base classes in the order they are specified in the derived class.
2. **Merge MROs**: Merge the MROs of the parent classes with the list of the derived class’s parent classes.
3. **Remove duplicates**: Ensure that each class appears only once in the final MRO list.

**Example:**

```python
class A:
    def method(self):
        print("Method from A")

class B(A):
    def method(self):
        print("Method from B")

class C(A):
    def method(self):
        print("Method from C")

class D(B, C):
    pass

print(D.__mro__)
# Output: (<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>)
```

In this example:

- The MRO for class `D` is `[D, B, C, A, object]`, reflecting the order in which methods are resolved.

##### Using `super()` with MRO

The `super()` function interacts with the MRO to call methods from base classes in the correct order. This function is used to ensure that the method resolution follows the MRO and that each class’s method is called appropriately.

**Example:**

```python
class A:
    def __init__(self):
        print("Initializing A")

class B(A):
    def __init__(self):
        super().__init__()
        print("Initializing B")

class C(A):
    def __init__(self):
        super().__init__()
        print("Initializing C")

class D(B, C):
    def __init__(self):
        super().__init__()
        print("Initializing D")

d = D()
```

In this example:

- `super()` ensures that the `__init__` methods of `A`, `B`, and `C` are called in the order specified by the MRO, which is `A` → `B` → `C` → `D`.

##### Other Mechanisms Related to MRO

- **`__mro__` Attribute**: Provides the MRO of a class as a tuple. It lists the classes in the order they are considered for method resolution.
  
  ```python
  print(D.__mro__)
  # Output: (<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>)
  ```

- **`mro()` Method**: Returns the MRO of a class as a list. It is a method of the class type that provides the same information as `__mro__`.
  
  ```python
  print(D.mro())
  # Output: [<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>]
  ```

- **Method Resolution**: When a method is called on an instance, Python uses the MRO to find the method definition, starting from the class of the instance and moving through the MRO.

The Method Resolution Order (MRO) is a critical aspect of multiple inheritance in Python, ensuring that methods and attributes are resolved in a consistent and predictable manner. The C3 linearization algorithm is used to compute the MRO, merging parent MROs and maintaining order. The `super()` function interacts with the MRO to provide proper method resolution across the class hierarchy. Understanding MRO and related mechanisms is essential for designing complex class structures and managing inheritance in Python effectively.

#### Multi-level inheritance

Multi-level inheritance is a type of inheritance where a class inherits from a class that is itself derived from another class. This creates a chain of inheritance, forming a hierarchy.

##### How Multi-Level Inheritance Works

In multi-level inheritance, the derived class inherits attributes and methods from its parent class, which in turn inherits from another class. This chain can be extended further if needed.

Here's a basic example to illustrate multi-level inheritance:

```python
class Grandparent:
    def __init__(self):
        print("Grandparent initialized")

    def method_grandparent(self):
        print("Method from Grandparent")

class Parent(Grandparent):
    def __init__(self):
        super().__init__()  # Call to Grandparent's __init__
        print("Parent initialized")

    def method_parent(self):
        print("Method from Parent")

class Child(Parent):
    def __init__(self):
        super().__init__()  # Call to Parent's __init__
        print("Child initialized")

    def method_child(self):
        print("Method from Child")

# Create an instance of Child
child_instance = Child()
child_instance.method_grandparent()  # Inherited from Grandparent
child_instance.method_parent()       # Inherited from Parent
child_instance.method_child()        # Defined in Child
```

1. **Grandparent Class**: This is the base class from which all other classes derive.
2. **Parent Class**: Inherits from `Grandparent` and can access its methods and attributes. It also introduces its own methods.
3. **Child Class**: Inherits from `Parent`, thus also inheriting the functionality of `Grandparent`. It adds its own methods and can use those inherited from both `Parent` and `Grandparent`.

<img title="" src="../_assets/multilevel_inheritance.svg" alt="multi-level inheritance" data-align="center">

##### Key Points

- **Method Resolution Order (MRO)**: Python uses the C3 linearization algorithm to determine the method resolution order in multi-level inheritance. This ensures a consistent order in which methods are resolved, which is essential when dealing with multiple levels of inheritance.

- **Use of `super()`**: In multi-level inheritance, the `super()` function is used to ensure that methods from parent classes are properly called. It allows for calling methods in the method resolution order.

#### Diamond Problem

The **diamond problem** occurs when two base classes of a derived class have a common ancestor, leading to ambiguity in method resolution. Python’s MRO algorithm is designed to handle this problem by providing a consistent method resolution order.

<img src="../_assets/diamond_problem_1.svg" title="" alt="diamond problem" data-align="center">

**Example:**

```python
class A:
    def method(self):
        print("Method from A")

class B(A):
    def method(self):
        print("Method from B")

class C(A):
    def method(self):
        print("Method from C")

class D(B, C):
    pass

d = D()
d.method()  # Output: Method from B
```

In this example:

- `D` inherits from both `B` and `C`, which both inherit from `A`.
- The MRO ensures that the method from `B` is chosen before `C` and `A`.

<img src="../_assets/diamond_problem.svg" title="" alt="diamond problem in python" data-align="center">

#### Using `super()` in Multiple Inheritance

The `super()` function works with multiple inheritance to ensure that all parent classes are correctly initialized and that their methods are called in the proper order.

**Example:**

```python
class A:
    def __init__(self):
        print("Initializing A")

class B(A):
    def __init__(self):
        super().__init__()
        print("Initializing B")

class C(A):
    def __init__(self):
        super().__init__()
        print("Initializing C")

class D(B, C):
    def __init__(self):
        super().__init__()
        print("Initializing D")

d = D()
```

In this example:

- The `super()` function ensures that `A`'s `__init__` method is called once, even though `D` inherits from both `B` and `C`.

#### Best Practices for Multiple Inheritance

- **Use sparingly**: Multiple inheritance can lead to complex and difficult-to-maintain code. Use it only when it provides a clear benefit.
- **Prefer composition over inheritance**: In many cases, composition (using objects of other classes) can achieve similar results without the complexity of multiple inheritance.
- **Be aware of the MRO**: Understand how Python’s MRO works to avoid unintended behavior and ambiguity.

Multiple inheritance in Python allows a class to inherit from multiple base classes, enabling the combination of various functionalities. While it offers significant flexibility, it also introduces complexities such as the diamond problem and requires careful management of the method resolution order. Using `super()` helps handle multiple inheritance scenarios more effectively, ensuring proper initialization and method calls across the class hierarchy.

### Method Overriding

**Method overriding** is a fundamental concept in object-oriented programming (OOP) where a subclass provides a specific implementation of a method that is already defined in its superclass. This allows subclasses to customize or extend the behavior of methods inherited from parent classes. 

When a method in a subclass has the same name, parameters, and return type as a method in its superclass, the subclass method overrides the superclass method. This means that when the method is called on an instance of the subclass, the overridden method in the subclass is executed instead of the method in the superclass.

**Key Points:**

- **Same Signature**: The overriding method must have the same name and signature (parameters) as the method in the superclass.
- **Accessing Superclass Methods**: The overridden method can call the method in the superclass using `super()`, allowing it to extend or modify its behavior.

#### How Method Overriding Works in Python

In Python, method overriding is implemented by defining a method in the subclass with the same name as the method in the superclass. When the method is called on an instance of the subclass, Python will use the subclass’s method.

**Example:**

```python
class Animal:
    def make_sound(self):
        print("Some generic animal sound")

class Dog(Animal):
    def make_sound(self):
        print("Woof!")

# Creating instances
generic_animal = Animal()
dog = Dog()

# Calling methods
generic_animal.make_sound()  # Output: Some generic animal sound
dog.make_sound()            # Output: Woof!
```

In this example:

- `Dog` overrides the `make_sound` method of `Animal`. 
- When `make_sound` is called on an instance of `Dog`, it executes the overridden method in `Dog`, not the method in `Animal`.

#### Accessing Superclass Methods

Sometimes, you may want to call the original method in the superclass from the overridden method to extend or modify its behavior. This can be done using the `super()` function.

**Example:**

```python
class Animal:
    def make_sound(self):
        print("Some generic animal sound")

class Dog(Animal):
    def make_sound(self):
        super().make_sound()  # Calling the method in Animal
        print("Woof!")

# Creating instance
dog = Dog()

# Calling method
dog.make_sound()
# Output:
# Some generic animal sound
# Woof!
```

In this example:

- `super().make_sound()` calls the `make_sound` method in the `Animal` class, and then the `Woof!` message is printed by the `Dog` class.

#### Use Cases for Method Overriding

**1. Customizing Behavior:** Allows subclasses to provide specific behavior different from the superclass.
**2. Extending Functionality:** Subclasses can add new behavior while reusing the existing functionality of the superclass.
**3. Polymorphism:** Supports polymorphic behavior where different subclasses provide their own implementations of the same method.

**Example in Data Engineering:**

```python
class DataProcessor:
    def process_data(self, data):
        print("Processing data in the generic way")

class CSVDataProcessor(DataProcessor):
    def process_data(self, data):
        super().process_data(data)  # Calling the generic processing
        print("Processing data in CSV-specific way")

# Creating instance
csv_processor = CSVDataProcessor()

# Calling method
csv_processor.process_data("data.csv")
# Output:
# Processing data in the generic way
# Processing data in CSV-specific way
```

In this example:

- `CSVDataProcessor` overrides the `process_data` method to include CSV-specific processing, while also calling the generic processing logic from the `DataProcessor` class.

#### Best Practices for Method Overriding

- **Maintain Consistency:** Ensure that the overridden method has the same signature as the method in the superclass to avoid confusion.
- **Document Overrides:** Clearly document why and how the method is overridden to maintain code readability.
- **Use `super()` Wisely:** Use `super()` to extend the functionality of the superclass method rather than completely replacing it, when applicable.
- **Consider `@Override` Decorator:** Python does not have a built-in `@Override` decorator like Java, but you can use comments or custom decorators to indicate overridden methods for clarity.

Method overriding is a powerful feature in Python that allows subclasses to provide specific implementations of methods defined in their superclasses. By overriding methods, you can customize behavior, extend functionality, and achieve polymorphic behavior. Understanding how to properly use and manage method overriding is crucial for effective object-oriented design and coding in Python.

### Mixin

In object-oriented programming, [mixins]([The Digital Cat - Multiple inheritance and mixin classes in Python](https://www.thedigitalcatonline.com/blog/2020/03/27/mixin-classes-in-python/)) are a powerful design pattern used to add specific functionalities to classes in a modular and reusable manner. Unlike traditional inheritance, which establishes a hierarchical relationship between classes, mixins offer a way to compose classes with multiple behaviors without enforcing an "is-a" relationship. This allows developers to write more modular code by mixing in various functionalities into a class, promoting code reuse and reducing duplication. The concept of mixins is particularly useful in Python due to its dynamic nature and flexible class system, enabling the combination of different features into a single class seamlessly.

The primary advantage of mixins lies in their ability to add common functionality to multiple classes without forcing an inheritance chain. For example, instead of creating a complex inheritance hierarchy to include logging, caching, or authentication functionalities, you can define separate mixin classes that provide these features independently. By applying these mixins to any class that needs them, you maintain a clean and manageable codebase while enhancing the functionality of your classes. This approach not only promotes code reuse but also facilitates the testing and maintenance of individual functionalities.

Despite their advantages, mixins require careful consideration to avoid potential pitfalls such as method conflicts and increased complexity. Since mixins can be applied to multiple classes, managing method resolution and ensuring compatibility between mixins can become challenging. Additionally, excessive use of mixins may lead to a phenomenon known as the "diamond problem," where ambiguities arise in method resolution when a class inherits from multiple mixins that provide conflicting implementations. Therefore, while mixins offer significant benefits in terms of modularity and flexibility, they should be used judiciously to maintain a well-structured and understandable codebase.

#### Key Concepts

**Purpose of Mixins**:

- **Code Reusability**: Mixins allow for the reuse of code across different classes without duplication.
- **Separation of Concerns**: By using mixins, different functionalities can be compartmentalized into separate classes, making code more modular and easier to maintain.

**Characteristics of Mixins**:

- **Single Responsibility**: A mixin class typically focuses on a single piece of functionality or behavior.
- **No Inheritance Hierarchy**: Mixins should not form part of a deep inheritance hierarchy. Instead, they are meant to be used in combination with other classes.
- **No Direct Instantiation**: Mixins are usually not intended to be instantiated directly. They are meant to be used as components in other classes.

#### Implementing Mixins in Python

In Python, mixins are implemented as base classes that provide specific methods or attributes. They are then combined with other classes through multiple inheritance.

##### Example: Logging Mixin

Let's create a `LoggingMixin` that provides logging functionality to any class that needs it.

```python
import logging

# Define the mixin
class LoggingMixin:
    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.logger = logging.getLogger(self.__class__.__name__)
        self.logger.setLevel(logging.DEBUG)

    def log(self, message):
        self.logger.debug(message)

# Define a class that uses the mixin
class DataProcessor(LoggingMixin):
    def __init__(self, name):
        super().__init__()
        self.name = name

    def process(self):
        self.log(f"Processing data with {self.name}")
        # Implement data processing logic here

# Example usage
if __name__ == "__main__":
    logging.basicConfig(level=logging.DEBUG)
    processor = DataProcessor("Processor1")
    processor.process()
```

#### Explanation:

- **LoggingMixin**: Provides logging capabilities. It initializes a logger and provides a `log` method.
- **DataProcessor**: Inherits from `LoggingMixin` and uses its logging capabilities to log messages.
- **Usage**: When `DataProcessor` is instantiated and its `process` method is called, it logs a message indicating that it is processing data.

#### Benefits of Mixins

1. **Flexibility**: Mixins can be combined in various ways to compose different functionalities in a class.
2. **Avoids Duplication**: Allows reuse of code across multiple classes without duplicating logic.
3. **Improves Readability**: Makes classes more readable and maintainable by separating concerns into distinct mixins.

#### Challenges with Mixins

1. **Complexity**: Using multiple mixins can lead to complex and hard-to-follow class hierarchies.
2. **Method Conflicts**: If different mixins provide methods with the same name, it can lead to conflicts and unexpected behavior.

Mixins provide a powerful way to share functionality across different classes, enhancing code reusability and modularity. However, they should be used thoughtfully to avoid potential pitfalls such as increased complexity and method conflicts.

### Inheritance Example: Put all togather

```python
# Base class for single inheritance
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} makes a sound")

# Derived class demonstrating single inheritance
class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)  # Call constructor of base class
        self.breed = breed

    def speak(self):
        print(f"{self.name} barks")

    def display_info(self):
        print(f"Name: {self.name}, Breed: {self.breed}")

# Another base class for multiple inheritance
class Swimmer:
    def swim(self):
        print("I can swim")

# Multiple inheritance example
class Dolphin(Dog, Swimmer):
    def __init__(self, name, breed, is_wild):
        super().__init__(name, breed)  # Initialize from Dog
        self.is_wild = is_wild

    def speak(self):
        super().speak()  # Call speak method from Dog
        print("Dolphin clicks")

    def display_info(self):
        super().display_info()  # Call display_info from Dog
        print(f"Is wild: {self.is_wild}")

# Base class for multi-level inheritance
class Vehicle:
    def __init__(self, brand):
        self.brand = brand

    def display(self):
        print(f"Brand: {self.brand}")

# Intermediate class in multi-level inheritance
class Car(Vehicle):
    def __init__(self, brand, model):
        super().__init__(brand)
        self.model = model

    def display(self):
        super().display()
        print(f"Model: {self.model}")

# Derived class in multi-level inheritance
class SportsCar(Car):
    def __init__(self, brand, model, top_speed):
        super().__init__(brand, model)
        self.top_speed = top_speed

    def display(self):
        super().display()
        print(f"Top Speed: {self.top_speed} km/h")

# Example usage
if __name__ == "__main__":
    # Single inheritance example
    my_dog = Dog("Rex", "German Shepherd")
    my_dog.speak()          # Output: Rex barks
    my_dog.display_info()  # Output: Name: Rex, Breed: German Shepherd

    # Multiple inheritance example
    my_dolphin = Dolphin("Flipper", "Bottlenose", True)
    my_dolphin.speak()      # Output: Flipper barks
                            #         Dolphin clicks
    my_dolphin.display_info()  # Output: Name: Flipper, Breed: Bottlenose
                               #         Is wild: True

    # Multi-level inheritance example
    my_sports_car = SportsCar("Ferrari", "488", 330)
    my_sports_car.display()  # Output: Brand: Ferrari
                              #         Model: 488
                              #         Top Speed: 330 km/h
```

#### Comments on the Code:

- **Single Inheritance**: `Dog` class inherits from `Animal`, demonstrating method overriding and calling base class methods using `super()`.

- **Multiple Inheritance**: `Dolphin` class inherits from both `Dog` and `Swimmer`, illustrating how `super()` is used to manage multiple base classes and method resolution.

- **Multi-Level Inheritance**: `SportsCar` class inherits from `Car`, which in turn inherits from `Vehicle`, showing how to extend functionality across multiple levels of inheritance.

<img src="../_assets/python_inheritance_example.svg" title="" alt="inheritance in python" data-align="center">

### Inheritance in data pipelines

Inheritance in data pipelines allows for the creation of flexible and reusable components, which is crucial in designing robust and scalable data engineering solutions. Here’s an example demonstrating how inheritance can be applied to a data pipeline system for a data engineer:

#### Example: Basic Data Pipeline Framework with Inheritance

In this example, we will design a simple data pipeline framework using inheritance. The framework will have base and derived classes for different stages of the pipeline: data extraction, transformation, and loading.

```python
# Base class for a pipeline component
class PipelineComponent:
    def __init__(self, name):
        self.name = name

    def process(self, data):
        # Base class implementation (does nothing)
        return data

    def __str__(self):
        return f"{self.__class__.__name__} - {self.name}"

# Derived class for data extraction
class DataExtractor(PipelineComponent):
    def __init__(self, name, source):
        super().__init__(name)
        self.source = source

    def process(self, data):
        # Simulate data extraction from a source
        print(f"Extracting data from {self.source}")
        return data  # For simplicity, we're returning the same data

# Derived class for data transformation
class DataTransformer(PipelineComponent):
    def __init__(self, name, transformation_rule):
        super().__init__(name)
        self.transformation_rule = transformation_rule

    def process(self, data):
        # Simulate data transformation
        print(f"Transforming data using rule: {self.transformation_rule}")
        return [self.transformation_rule(item) for item in data]

# Derived class for data loading
class DataLoader(PipelineComponent):
    def __init__(self, name, destination):
        super().__init__(name)
        self.destination = destination

    def process(self, data):
        # Simulate data loading into a destination
        print(f"Loading data to {self.destination}")
        # Assume the data is loaded successfully
        return data

# Example usage
if __name__ == "__main__":
    # Create instances of each pipeline component
    extractor = DataExtractor(name="Extractor1", source="Database")
    transformer = DataTransformer(name="Transformer1", transformation_rule=lambda x: x.upper())
    loader = DataLoader(name="Loader1", destination="Data Warehouse")

    # Simulate a pipeline execution
    data = ["data1", "data2", "data3"]
    print("Pipeline Execution:")
    data = extractor.process(data)
    data = transformer.process(data)
    loader.process(data)
```

### Explanation:

- **PipelineComponent**: This is the base class for all pipeline components. It includes a `process()` method that is meant to be overridden by derived classes. In this simplified version, `process()` in the base class does nothing and simply returns the data.

- **DataExtractor**: Inherits from `PipelineComponent`. Implements the `process()` method to simulate data extraction from a source. It demonstrates how you can extend functionality in derived classes.

- **DataTransformer**: Inherits from `PipelineComponent`. Implements the `process()` method to transform data using a specified transformation rule. It shows how to add specific behavior to a component.

- **DataLoader**: Inherits from `PipelineComponent`. Implements the `process()` method to simulate loading data into a destination. It illustrates how to handle data loading in the pipeline.

<img src="../_assets/inheritance_in_datapipelines_example.svg" title="" alt="" data-align="center">

### Benefits of Using Inheritance in This Example:

1. **Code Reusability**: Common functionality (e.g., initialization and basic processing) is handled in the base class, avoiding code duplication in derived classes.

2. **Flexibility**: New stages or components can be easily added by creating new classes that inherit from the `PipelineComponent` base class.

3. **Maintainability**: By centralizing common logic in the base class, it becomes easier to update and maintain the code.

4. **Clarity**: Using inheritance makes it clear that different pipeline components share common functionality while providing their own specific behavior.

This example illustrates how inheritance can be used to create a simple yet flexible data pipeline system, making it easier for data engineers to build and manage data processing workflows.

---

## 3. Abstraction

### Introduction to Abstraction and Its Applications

Abstraction is a fundamental concept in computer science and object-oriented programming (OOP) that focuses on simplifying complex systems by hiding the implementation details and exposing only the essential features. At its core, abstraction allows developers to manage complexity by providing a high-level interface for interacting with objects or systems, while concealing the intricate workings behind the scenes. This process of abstracting away the details helps in designing systems that are more modular, easier to maintain, and less prone to errors. By focusing on what an object does rather than how it achieves its functionality, abstraction facilitates a more intuitive approach to programming and system design.

In practical applications, abstraction is widely used to create a clear separation between the high-level operations and the low-level implementation details. For instance, consider a public transportation system. Users of the system interact with a simplified interface, such as a ticket purchasing machine or a mobile app, without needing to understand the complexities involved in the scheduling, routing, and vehicle management that happens behind the scenes. Similarly, in software development, abstraction enables programmers to work with high-level constructs like classes and methods, without delving into the nitty-gritty details of the underlying code or algorithms.

In the context of data pipelines, abstraction plays a crucial role in designing and managing data workflows. Data pipelines often involve multiple stages, each with specific tasks such as data ingestion, transformation, validation, and loading into storage systems. By using abstraction, data engineers can create high-level interfaces or components for each stage of the pipeline, while hiding the implementation details. For example, a data pipeline might use abstract components for reading data from various sources, such as APIs or databases, and abstract components for transforming and aggregating data. This separation allows engineers to focus on the overall data flow and processing logic without being bogged down by the specifics of each data source or transformation.

A practical use case for abstraction in data pipelines is the development of a unified data processing framework. Imagine a scenario where a company needs to integrate data from different sources, including relational databases, CSV files, and web APIs. By defining abstract interfaces for each data source, the company can create a consistent and cohesive data pipeline architecture. This approach allows for easy integration of new data sources in the future, as long as they adhere to the predefined abstract interfaces. As a result, the pipeline remains flexible and adaptable to changing requirements, without requiring major overhauls each time a new data source is introduced.

Moreover, abstraction in data pipelines also enhances code maintainability and readability. By defining clear abstract interfaces for various pipeline components, engineers can write modular code that is easier to test and debug. For instance, if an issue arises with data transformation, engineers can focus on the specific transformation component, knowing that the data ingestion and loading components operate independently. This modularity helps in isolating problems and implementing fixes more efficiently, leading to a more robust and reliable data pipeline.

Abstraction is a powerful concept that simplifies complex systems by providing a high-level interface while hiding implementation details. Its applications in data pipelines allow for more modular, flexible, and maintainable code. By leveraging abstraction, data engineers can design efficient and adaptable data workflows that integrate diverse data sources and processing tasks seamlessly.

### What is Abstraction?

Abstraction is the process of simplifying complex systems by breaking them into smaller, manageable pieces and focusing only on the relevant aspects. In programming, this means defining classes and methods that provide a high-level view of an object while hiding the underlying implementation details. In Python, abstraction is achieved through **abstract classes and methods**, which provide a framework for defining common **interfaces** while allowing subclasses to provide specific implementations. For example, consider a simple class representing a vehicle:

```python
class Vehicle:
    def start_engine(self):
        pass

    def stop_engine(self):
        pass
```

In this example, `Vehicle` is an abstract representation of a vehicle. It defines the methods `start_engine` and `stop_engine` but does not provide any implementation. This allows different types of vehicles to implement these methods according to their specific needs.

In Python, abstraction is implemented through various mechanisms that allow developers to define and work with high-level interfaces while hiding the implementation details. Here are the different types of abstraction available in Python:

### Creating an Abstract Base Class

In Python, abstraction is often implemented using abstract base classes (ABCs) from the `abc` module. **Abstract Base Classes (ABCs)** are a formal way to define abstract methods and properties that must be implemented by any subclass. They provide a way to define a common interface for a group of related classes, ensuring that all derived classes adhere to this interface. Here's how to define an abstract base class:

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

    @abstractmethod
    def perimeter(self):
        pass
```

In this example, `Shape` is an abstract **base class** with two abstract methods, `area` and `perimeter`. Subclasses of `Shape` **must** provide implementations for these methods.

### Abstract Methods

To use an abstract base class, you need to create subclasses that implement the abstract methods. For example:

```python
class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)
```

Here, `Rectangle` is a concrete class that inherits from `Shape` and provides implementations for `area` and `perimeter`.

### Abstract Properties

In addition to abstract methods, you can also define abstract properties using the `@property` decorator combined with the `@abstractmethod` decorator. This ensures that any subclass provides an implementation for the property:

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
    @property
    @abstractmethod
    def fuel_type(self):
        pass

class Car(Vehicle):
    @property
    def fuel_type(self):
        return "Petrol"

# Instantiate the Car class and access the fuel_type property
def main():
    my_car = Car()
    print(f"The fuel type of the car is: {my_car.fuel_type}")

if __name__ == "__main__":
    main()
```

### Abstract Method vs Abstract Properties

Abstract methods and abstract properties are both mechanisms provided by Python's `abc` (Abstract Base Classes) module to define a common interface for a group of related classes. However, they serve different purposes and have distinct characteristics.

| Feature            | Abstract Method                                         | Abstract Property                                          |
| ------------------ | ------------------------------------------------------- | ---------------------------------------------------------- |
| **Definition**     | Method without implementation                           | Property without implementation                            |
| **Syntax**         | Decorated with `@abstractmethod`                        | Decorated with `@property` and `@abstractmethod`           |
| **Implementation** | Subclasses must override and implement the method       | Subclasses must provide a concrete property implementation |
| **Usage**          | Defines behavior that must be implemented by subclasses | Defines an attribute that must be provided by subclasses   |
| **Callability**    | Can be called as a method                               | Accessed as an attribute                                   |

- **Abstract Method:** Ensures that all subclasses of a base class implement a specific behavior (e.g., a `process` method for various types of processors).

- **Abstract Property:** Ensures that all subclasses provide a specific attribute (e.g., a `name` property for various types of entities).

### Abstract Methods with Default Implementations

In Python’s object-oriented programming, abstract methods are typically used to define a method signature that **must** be implemented by concrete subclasses. However, sometimes it is useful to provide a default implementation of an abstract method while still enforcing that subclasses can override it if necessary. This concept is particularly useful when you want to define a common behavior that can be optionally customized by subclasses.

Abstract methods with default implementations are **methods** declared in an abstract class with a default implementation. Subclasses can use this default implementation or override it with their own implementation. This approach provides a base behavior that is common to all subclasses but still allows subclasses to provide a specific implementation if needed. It helps in avoiding code duplication and facilitates code reuse.

```python
from abc import ABC, abstractmethod

class AbstractBase(ABC):
    def abstract_method(self):
        """Provide a default implementation."""
        print("Default implementation of abstract_method")

class ConcreteClass(AbstractBase):
    def abstract_method(self):
        """Override the abstract method with a specific implementation."""
        print("Concrete implementation of abstract_method")

class AnotherConcreteClass(AbstractBase):
    # Inherits the default implementation from AbstractBase
    pass

# Testing the implementations
obj1 = ConcreteClass()
obj1.abstract_method()  # Outputs: Concrete implementation of abstract_method

obj2 = AnotherConcreteClass()
obj2.abstract_method()  # Outputs: Default implementation of abstract_method
```

### Using Abstract Base Classes with Multiple Inheritance

When using ABCs with multiple inheritance, a class can inherit abstract methods and properties from more than one abstract base class. This enables you to define a class that conforms to multiple interfaces or protocols.

**Example:**

```python
from abc import ABC, abstractmethod

class Readable(ABC):
    @abstractmethod
    def read(self):
        """Abstract method for reading"""
        pass

class Writable(ABC):
    @abstractmethod
    def write(self):
        """Abstract method for writing"""
        pass

class File(Readable, Writable):
    def read(self):
        print("Reading file...")

    def write(self):
        print("Writing file...")
```

#### Explanation

1. **Abstract Base Classes:**
   
   - **`Readable`** and **`Writable`** are abstract base classes defined using the `ABC` class from the `abc` module. They both contain one abstract method:
     - **`read`** in `Readable`
     - **`write`** in `Writable`
   - These methods are abstract, meaning they must be implemented by any concrete subclass.

2. **Concrete Class Implementation:**
   
   - **`File`** is a concrete class that inherits from both `Readable` and `Writable`. It provides concrete implementations for the abstract methods defined in both base classes:
     - **`read`** method prints "Reading file..."
     - **`write`** method prints "Writing file..."
   - By implementing these methods, `File` conforms to the interfaces defined by `Readable` and `Writable`.

3. **How It Works with Multiple Inheritance:**
   
   - **`File`** inherits from both `Readable` and `Writable`, meaning it must implement all abstract methods from both base classes. This is a key feature of multiple inheritance with ABCs: a subclass can inherit and implement methods from multiple base classes.
   - The use of multiple inheritance allows `File` to be both readable and writable, combining the functionalities of both abstract base classes.

### Considerations:

**Method Resolution Order (MRO):**

- Python uses the C3 linearization algorithm to determine the method resolution order. For the `File` class, the MRO is `File -> Readable -> Writable -> ABC`. This means Python will first look for methods in `File`, then in `Readable`, then `Writable`, and finally in `ABC` if needed.

**Combining Behaviors:**

- The `File` class demonstrates how you can combine behaviors from multiple abstract classes into a single concrete class. It effectively merges the functionality of reading and writing into one class.

**Abstract Methods Implementation:**

- When using multiple inheritance with ABCs, it's crucial to implement all abstract methods from each base class. Failure to do so will result in a `TypeError`, as the class will remain abstract and cannot be instantiated.

**Use Cases:**

- This approach is useful when you need a class to adhere to multiple interfaces or protocols. For instance, in file handling systems, a file might need to support both reading and writing operations. By using abstract base classes, you can define clear contracts for these operations and ensure that any concrete implementation adheres to these contracts.

---

## 4. Polymorphism in Python

**Polymorphism** is a core concept in object-oriented programming (OOP) that allows objects of different classes to be treated as objects of a common superclass. It enables a single function or method to operate on different types of objects, providing flexibility and reusability in code. This tutorial will guide you through polymorphism in Python, from basic to advanced levels.

Polymorphism is derived from Greek, meaning "**many forms.**" In programming, it refers to the ability to call the same method on different objects and have each of them respond in their own way. It allows you to use a unified interface for different underlying forms (data types).

### Basic Example of Polymorphism

In Python, polymorphism is achieved through **method overriding** and **duck typing**. Here's a simple example to illustrate:

```python
class Animal:
    def make_sound(self):
        raise NotImplementedError("Subclass must implement abstract method")

class Dog(Animal):
    def make_sound(self):
        return "Woof!"

class Cat(Animal):
    def make_sound(self):
        return "Meow!"

# Function that uses polymorphism
def animal_sound(animal):
    print(animal.make_sound())

# Usage
dog = Dog()
cat = Cat()

animal_sound(dog)  # Output: Woof!
animal_sound(cat)  # Output: Meow!
```

In this example:

- The `Animal` class defines an abstract method `make_sound`.
- The `Dog` and `Cat` classes override the `make_sound` method with specific implementations.
- The `animal_sound` function calls `make_sound` on any `Animal` object, demonstrating polymorphism.

### Method Overriding

When a method in a subclass has the same name, same parameters, and same return type as a method in its superclass, it is considered to override the superclass's method. This means that when the method is called on an instance of the subclass, the subclass's version of the method is executed, not the one from the superclass.

**Key Points:**

- The method in the subclass must have the same name as the method in the superclass.
- It must have the same or compatible parameters.
- The subclass method can call the superclass method using the `super()` function, if needed, to extend or modify its behavior.

**Benefits of Method Overriding:**

- **Specialization:** Allows subclasses to provide specialized behavior for methods inherited from a superclass.
- **Flexibility:** Enables dynamic method binding, where the method that gets executed is determined at runtime based on the object's class.
- **Code Reusability:** Promotes code reuse by allowing subclasses to reuse and extend the functionality of superclass methods.

### Polymorphism with Inheritance

Inheritance allows a class to inherit methods and attributes from another class. Polymorphism is often used with inheritance to allow subclasses to provide specific implementations of methods defined in a superclass.

```python
class Shape:
    def area(self):
        raise NotImplementedError("Subclass must implement abstract method")

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius * self.radius

# Function that uses polymorphism with inheritance
def print_area(shape):
    print(f"Area: {shape.area()}")

# Usage
rectangle = Rectangle(5, 10)
circle = Circle(7)

print_area(rectangle)  # Output: Area: 50
print_area(circle)     # Output: Area: 153.86
```

In this example:

- `Shape` is a superclass with an abstract `area` method.
- `Rectangle` and `Circle` provide specific implementations of the `area` method.
- The `print_area` function uses polymorphism to handle different `Shape` objects.

### Duck Typing

Python's dynamic nature means that objects are not strictly required to inherit from a common superclass to be used interchangeably. This is known as duck typing: "**If it looks like a duck and quacks like a duck, it's a duck.**"

Duck typing is a programming concept where the type or class of an object is determined by its behavior (methods and properties) rather than its explicit inheritance from a specific class or interface. In other words, if an object implements the required methods and behaviors, it can be treated as an instance of the expected type, regardless of its actual class.

```python
class Bird:
    def fly(self):
        print("Flies high")

class Airplane:
    def fly(self):
        print("Soars through the sky")

class Boat:
    def sail(self):
        print("Sails on water")

def make_it_fly(flyable):
    flyable.fly()

# Usage
bird = Bird()
plane = Airplane()
boat = Boat()

make_it_fly(bird)  # Outputs: Flies high
make_it_fly(plane) # Outputs: Soars through the sky

# The following will raise an error because Boat does not have a fly method
# make_it_fly(boat)
```

In this example:

- Both `Bird` and `Airplane` have a `fly` method, so they can be used interchangeably in the `make_it_fly` function.
- The `Boat` class does not have a `fly` method, so it cannot be used with `make_it_fly`, demonstrating how duck typing depends on method availability rather than class inheritance.

Duck typing is especially useful in scenarios where you work with heterogeneous collections of objects or implement generic functions and algorithms that operate on different types of objects. Here are a few examples:

- **Data Processing:** Functions that process different types of data structures (e.g., lists, sets, dictionaries) can be designed to work with any object that supports the required methods.

- **Frameworks and Libraries:** Many Python frameworks and libraries rely on duck typing to provide flexibility and extensibility. For example, Django and Flask use duck typing for middleware and view functions.

- **Testing and Mocking:** Duck typing is useful in testing where mock objects can be created to simulate real objects, as long as they provide the expected methods.

  

```python
class EmailNotification:
    def send(self, message):
        print(f"Sending email: {message}")

class SMSNotification:
    def send(self, message):
        print(f"Sending SMS: {message}")

class PushNotification:
    def send(self, message):
        print(f"Sending push notification: {message}")

def notify(notifier, message):
    notifier.send(message)

# Usage
email = EmailNotification()
sms = SMSNotification()
push = PushNotification()

notify(email, "Hello via Email!")
notify(sms, "Hello via SMS!")
notify(push, "Hello via Push Notification!")

```

### Method Overloading and Polymorphism

While Python does not support traditional method overloading (having multiple methods with the same name but different signatures), it does support polymorphism through default arguments and variable-length argument lists.

```python
class Printer:
    def print_message(self, message, times=1):
        for _ in range(times):
            print(message)

# Usage
printer = Printer()
printer.print_message("Hello")          # Output: Hello
printer.print_message("Hello", 3)       # Output: Hello Hello Hello
```

In this example:

- The `print_message` method can handle different numbers of arguments, demonstrating polymorphism with default arguments.

### Polymorphism with Operator Overloading

**Operator overloading**, or operator overriding, is a feature in Python that allows developers to define custom behavior for standard operators (like `+`, `-`, `*`, etc.) in user-defined classes. This feature is a form of polymorphism because it allows different objects to respond to the same operator in ways that are specific to their types.

Operator overloading enables you to define how operators behave with instances of your custom classes. This means you can customize the behavior of operators such as `+`, `-`, `*`, `/`, and others for your own objects. By doing this, you make your custom classes more intuitive and easier to use in expressions involving these operators.

**Key Points:**

- **Special Methods:** Python uses special methods, also known as **dunder (double underscore)** methods, to implement operator overloading. For example, `__add__` is used to overload the `+` operator.
- **Intuitive Syntax:** Overloading operators allows for a more natural and intuitive syntax when working with custom objects, improving code readability and usability.
- **Consistency:** By providing clear implementations for operators, you can ensure that your objects behave consistently in expressions and operations.

#### Implementing Operator Overloading

To implement operator overloading, you need to define special methods in your class. These methods are named using double underscores before and after the method name (e.g., `__add__`, `__sub__`, `__mul__`). Here’s how you can overload the `+` operator using the `__add__` method:

**Example: Overloading the `+` Operator**

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
    
    def __repr__(self):
        return f"Vector({self.x}, {self.y})"

# Usage
v1 = Vector(1, 2)
v2 = Vector(3, 4)
result = v1 + v2
print(result)  # Outputs: Vector(4, 6)
```

In this example:

- **`__init__` Method:** Initializes the `Vector` class with `x` and `y` coordinates.
- **`__add__` Method:** Defines how the `+` operator should work when applied to `Vector` instances. It adds the corresponding components of the vectors.
- **`__repr__` Method:** Provides a string representation of the `Vector` instance for easier debugging and printing.

#### Other Operators You Can Overload

In addition to `+`, you can overload many other operators by defining their corresponding special methods:

- **Arithmetic Operators:** `__sub__` (for `-`), `__mul__` (for `*`), `__truediv__` (for `/`), etc.
- **Comparison Operators:** `__eq__` (for `==`), `__ne__` (for `!=`), `__lt__` (for `<`), `__le__` (for `<=`), `__gt__` (for `>`), `__ge__` (for `>=`).
- **Unary Operators:** `__neg__` (for unary `-`), `__pos__` (for unary `+`), `__abs__` (for `abs()` function).
- **Other Operators:** `__getitem__` (for indexing `[]`), `__setitem__` (for setting items), `__call__` (for calling instances as functions).

**Example: Overloading Comparison Operators**

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def __eq__(self, other):
        return self.x == other.x and self.y == other.y
    
    def __lt__(self, other):
        return (self.x**2 + self.y**2) < (other.x**2 + other.y**2)
    
    def __repr__(self):
        return f"Point({self.x}, {self.y})"

# Usage
p1 = Point(1, 2)
p2 = Point(1, 2)
p3 = Point(3, 4)

print(p1 == p2)  # Outputs: True
print(p1 < p3)   # Outputs: True
```

In this example:

- **`__eq__` Method:** Defines equality comparison for `Point` objects.
- **`__lt__` Method:** Defines less-than comparison based on the distance from the origin.

#### Use Cases and Applications

Operator overloading can be particularly useful in several scenarios:

- **Mathematical Objects:** Custom classes representing mathematical entities (like vectors, matrices, complex numbers) can overload arithmetic operators to simplify mathematical operations.
- **Data Structures:** Classes implementing data structures (like matrices, polynomials) benefit from operator overloading to make them more intuitive to use.
- **Domain-Specific Languages (DSLs):** Operator overloading can be used to create domain-specific languages or mini-languages where operations are customized for specific types of data.

**Example: Implementing a Matrix Class with Operator Overloading**

```python
class Matrix:
    def __init__(self, rows):
        self.rows = rows
    
    def __add__(self, other):
        return Matrix([[self.rows[i][j] + other.rows[i][j] for j in range(len(self.rows[0]))] for i in range(len(self.rows))])
    
    def __repr__(self):
        return '\n'.join(['\t'.join(map(str, row)) for row in self.rows])

# Usage
m1 = Matrix([[1, 2], [3, 4]])
m2 = Matrix([[5, 6], [7, 8]])
result = m1 + m2
print(result)
```

In this example:

- **Matrix Addition:** The `__add__` method allows for matrix addition using the `+` operator, making matrix operations more intuitive.

### Abstract Base Classes and Polymorphism

Abstract Base Classes (ABCs) provide a formal way to define and enforce interfaces, which can be used to achieve polymorphism.

```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def make_sound(self):
        pass

class Dog(Animal):
    def make_sound(self):
        return "Woof!"

class Cat(Animal):
    def make_sound(self):
        return "Meow!"

def animal_sound(animal):
    print(animal.make_sound())

# Usage
animals = [Dog(), Cat()]

for animal in animals:
    animal.make_sound()
    
# Output: Woof!
# Output: Meow!
```

In this example:

- `Animal` is an abstract base class with an abstract method `make_sound`.
- `Dog` and `Cat` implement the `make_sound` method.
- This setup allows the `animal_sound` function to operate on any `Animal`, demonstrating polymorphism with ABCs.

Polymorphism in Python allows methods and functions to operate on objects of different types in a uniform way. It can be achieved through inheritance, duck typing, method overloading, operator overloading, and abstract base classes. This tutorial has covered the basics of polymorphism, provided examples of its application, and explored advanced topics such as operator overloading and abstract base classes. By understanding and utilizing polymorphism, you can write more flexible and reusable code, making your programs easier to maintain and extend.



## Encapsulation vs Inheritance vs Abstraction vs Polymorphism



| **Concept**       | **Definition**                                               | **Purpose**                                                  | **Key Features**                                             | **Use Cases**                                                |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Encapsulation** | Bundling data and methods that operate on the data into a single unit (class) and restricting access to some of the object's components. | To protect the internal state of an object from unintended or harmful changes and to provide a controlled interface. | - Access modifiers (public, protected, private) <br> - Property decorators <br> - Getter and setter methods | - Data hiding <br> - Restricting direct access <br> - Implementing controlled interfaces |
| **Inheritance**   | Mechanism by which one class (child) inherits attributes and methods from another class (parent). | To promote code reusability and establish a hierarchical relationship between classes. | - Single, multiple, and multi-level inheritance <br> - Method overriding <br> - `super()` usage | - Extending functionality <br> - Creating hierarchical models <br> - Code reuse |
| **Abstraction**   | Hiding the complex implementation details and showing only the essential features of the object. | To simplify interaction with complex systems and to provide a clear and focused interface. | - Abstract classes <br> - Abstract methods <br> - Concrete subclasses implementing abstract methods | - Simplifying complex systems <br> - Defining clear interfaces <br> - Modular design |
| **Polymorphism**  | The ability of different objects to be treated as instances of the same class through a common interface. | To allow objects of different classes to be treated through a common interface, enhancing flexibility. | - Method overriding <br> - Method overloading <br> - Duck typing <br> - Operator overloading | - Implementing common interfaces <br> - Dynamic method invocation <br> - Enhancing flexibility in code |



- **Encapsulation** focuses on bundling data with methods and restricting access to the internals of an object. It ensures that the internal state of an object is protected and provides controlled access through public methods. Encapsulation helps in maintaining and modifying the internal structure of a class without affecting the outside code.

- **Inheritance** allows one class to inherit attributes and methods from another class. This promotes code reuse and establishes a parent-child relationship between classes. Inheritance can be single, multiple, or multi-level, and it helps in extending functionality and creating hierarchical models.

- **Abstraction** hides the complex implementation details and exposes only the essential features of an object. It is achieved through abstract classes and methods. Abstraction simplifies interactions with complex systems by defining clear and focused interfaces, making it easier to work with and manage complex systems.

- **Polymorphism** enables objects of different classes to be treated as instances of the same class through a common interface. This includes method overriding, method overloading, and operator overloading. Polymorphism enhances code flexibility and allows dynamic method invocation based on the object's actual type at runtime.

## Example: Put all togather:

Below is a simple data pipeline project that demonstrates the core Object-Oriented Programming (OOP) concepts: **Encapsulation, Inheritance, Abstraction, and Polymorphism.** The project involves a basic data processing pipeline where data is read, processed, and written.

**Objective:** Create a data pipeline that reads data from a source, processes it, and writes the processed data to a destination. Use OOP principles to structure the code.

#### 1. Abstraction

We will use abstract classes to define the common interface for different types of data sources and data processors.

```python
from abc import ABC, abstractmethod

# Abstract base class for data sources
class DataSource(ABC):
    @abstractmethod
    def read(self):
        pass

# Abstract base class for data processors
class DataProcessor(ABC):
    @abstractmethod
    def process(self, data):
        pass

# Abstract base class for data destinations
class DataDestination(ABC):
    @abstractmethod
    def write(self, data):
        pass
```

#### 2. Encapsulation

Encapsulation is demonstrated by defining how the data is managed within each class. We'll create concrete implementations of the abstract classes that encapsulate the data handling logic.

```python
# Concrete class for reading from a file
class FileDataSource(DataSource):
    def __init__(self, filename):
        self.filename = filename

    def read(self):
        with open(self.filename, 'r') as file:
            return file.readlines()

# Concrete class for processing data by converting it to uppercase
class UpperCaseProcessor(DataProcessor):
    def process(self, data):
        return [line.upper() for line in data]

# Concrete class for writing data to a file
class FileDataDestination(DataDestination):
    def __init__(self, filename):
        self.filename = filename

    def write(self, data):
        with open(self.filename, 'w') as file:
            file.writelines(data)
```

#### 3. Inheritance

Inheritance is used to create specialized versions of the abstract base classes. The concrete classes inherit from the abstract base classes and provide implementations for the abstract methods.

```python
# Inheriting from DataSource to implement file reading
class FileDataSource(DataSource):
    ...

# Inheriting from DataProcessor to implement data processing
class UpperCaseProcessor(DataProcessor):
    ...

# Inheriting from DataDestination to implement file writing
class FileDataDestination(DataDestination):
    ...
```

#### 4. Polymorphism

Polymorphism is demonstrated when different concrete implementations of the abstract classes are used interchangeably in the data pipeline.

```python
def run_pipeline(data_source: DataSource, processor: DataProcessor, destination: DataDestination):
    # Read data from the source
    data = data_source.read()
    
    # Process the data
    processed_data = processor.process(data)
    
    # Write the processed data to the destination
    destination.write(processed_data)

# Usage
if __name__ == "__main__":
    source = FileDataSource('input.txt')
    processor = UpperCaseProcessor()
    destination = FileDataDestination('output.txt')
    
    run_pipeline(source, processor, destination)
```



1. **Abstraction:** Defined the common interface for data sources, processors, and destinations using abstract base classes.
2. **Encapsulation:** Implemented specific behaviors for reading, processing, and writing data within concrete classes.
3. **Inheritance:** Used inheritance to extend abstract base classes and provide concrete implementations.
4. **Polymorphism:** Utilized polymorphism by defining a `run_pipeline` function that operates on any concrete implementations of the abstract classes.

This project showcases how to use core OOP concepts to structure and manage a simple data processing pipeline efficiently.



**The complete code** for the classes that inherit from `DataSource`, `DataProcessor`, and `DataDestination` to implement file reading, data processing, and file writing:

```python
from abc import ABC, abstractmethod

# Abstract base class for data sources
class DataSource(ABC):
    @abstractmethod
    def read(self):
        pass

# Abstract base class for data processors
class DataProcessor(ABC):
    @abstractmethod
    def process(self, data):
        pass

# Abstract base class for data destinations
class DataDestination(ABC):
    @abstractmethod
    def write(self, data):
        pass

# Inheriting from DataSource to implement file reading
class FileDataSource(DataSource):
    def __init__(self, filename):
        self.filename = filename

    def read(self):
        with open(self.filename, 'r') as file:
            return file.readlines()

# Inheriting from DataProcessor to implement data processing
class UpperCaseProcessor(DataProcessor):
    def process(self, data):
        return [line.upper() for line in data]

# Inheriting from DataDestination to implement file writing
class FileDataDestination(DataDestination):
    def __init__(self, filename):
        self.filename = filename

    def write(self, data):
        with open(self.filename, 'w') as file:
            file.writelines(data)

# Function to run the pipeline
def run_pipeline(data_source: DataSource, processor: DataProcessor, destination: DataDestination):
    # Read data from the source
    data = data_source.read()
    
    # Process the data
    processed_data = processor.process(data)
    
    # Write the processed data to the destination
    destination.write(processed_data)

# Usage
if __name__ == "__main__":
    source = FileDataSource('input.txt')
    processor = UpperCaseProcessor()
    destination = FileDataDestination('output.txt')
    
    run_pipeline(source, processor, destination)
```

### Explanation:

1. **`FileDataSource`**:
   - Inherits from `DataSource`.
   - Implements the `read` method to read lines from a specified file.

2. **`UpperCaseProcessor`**:
   - Inherits from `DataProcessor`.
   - Implements the `process` method to convert each line of data to uppercase.

3. **`FileDataDestination`**:
   - Inherits from `DataDestination`.
   - Implements the `write` method to write lines of data to a specified file.

4. **`run_pipeline` function**:
   - Demonstrates polymorphism by accepting instances of any class that inherits from the abstract base classes.
   - Reads data from a source, processes it, and writes the processed data to a destination.

5. **Usage**:
   - Creates instances of `FileDataSource`, `UpperCaseProcessor`, and `FileDataDestination`.
   - Runs the pipeline to process data from 'input.txt' and save it to 'output.txt'.

This code showcases how OOP principles such as abstraction, encapsulation, inheritance, and polymorphism are used in a real-world data pipeline scenario.



## Dunder Methods

Dunder methods, also known as **magic methods** or special methods, are a set of predefined methods in Python that allow you to define the behavior of your objects in built-in operations. They are named with double underscores before and after their names (e.g., `__init__`, `__str__`, `__add__`).

1. **`__init__`**: 
   
   - **Purpose**: Called when an instance of the class is created.
   - **Usage**: Initialize instance attributes.
   - **Example**: 
     ```python
     class Person:
         def __init__(self, name, age):
             self.name = name
             self.age = age
     ```
   
2. **`__str__`**:
   - **Purpose**: Defines the string representation of the object, used by `print()` and `str()`.
   - **Usage**: Provide a user-friendly string representation.
   - **Example**:
     ```python
     class Person:
         def __str__(self):
             return f"{self.name}, Age: {self.age}"
     ```

3. **`__repr__`**:
   - **Purpose**: Defines the string representation for debugging, used by `repr()`.
   - **Usage**: Provide an unambiguous string representation of the object.
   - **Example**:
     ```python
     class Person:
         def __repr__(self):
             return f"Person(name={self.name!r}, age={self.age!r})"
     ```

4. **`__len__`**:
   - **Purpose**: Defines behavior for the `len()` function.
   - **Usage**: Return the length of the object.
   - **Example**:
     ```python
     class MyCollection:
         def __init__(self, items):
             self.items = items
         
         def __len__(self):
             return len(self.items)
     ```

5. **`__getitem__`**, **`__setitem__`**, **`__delitem__`**:
   
   - **Purpose**: Define behavior for indexing, setting, and deleting items in collections.
   - **Usage**: Access, modify, or delete elements using indexing syntax.
   - **Example**:
     ```python
     class MyList:
         def __init__(self):
             self._list = []
         
         def __getitem__(self, index):
             return self._list[index]
         
         def __setitem__(self, index, value):
             self._list[index] = value
         
         def __delitem__(self, index):
             del self._list[index]
     ```
   
6. **`__add__`, **`__sub__`**, **`__mul__`:
   
   - **Purpose**: Define behavior for arithmetic operations.
   - **Usage**: Implement custom behavior for addition, subtraction, multiplication, etc.
   - **Example**:
     
     ```python
     class Vector:
         def __init__(self, x, y):
             self.x = x
             self.y = y
         
         def __add__(self, other):
             return Vector(self.x + other.x, self.y + other.y)
         
         def __repr__(self):
             return f"Vector(x={self.x}, y={self.y})"
     ```
   
7. **`__eq__`, **`__lt__`**, **`__gt__`:
   
   - **Purpose**: Define behavior for comparison operations.
   - **Usage**: Implement custom comparison logic.
   - **Example**:
     ```python
     class Person:
         def __init__(self, name, age):
             self.name = name
             self.age = age
         
         def __eq__(self, other):
             return self.age == other.age
         
         def __lt__(self, other):
             return self.age < other.age
     ```
   
8. **`__call__`**:
   
   - **Purpose**: Allows an instance of a class to be called as a function.
   - **Usage**: Implement callable objects.
   - **Example**:
     ```python
     class Adder:
         def __init__(self, value):
             self.value = value
         
         def __call__(self, x):
             return self.value + x
     ```
   
9. **`__enter__`**, **`__exit__`**:
   
   - **Purpose**: Define behavior for context managers (used with `with` statement).
   - **Usage**: Manage resources, like files.
   - **Example**:
     ```python
     class FileOpener:
         def __init__(self, filename):
             self.filename = filename
         
         def __enter__(self):
             self.file = open(self.filename, 'r')
             return self.file
         
         def __exit__(self, exc_type, exc_val, exc_tb):
             self.file.close()
     ```

**Applications and Use Cases:**

- **Custom Data Structures**: Implement indexing, length, and item management in custom collections.
- **Operator Overloading**: Define how custom objects respond to arithmetic and comparison operators.
- **Context Management**: Manage resources using context managers to ensure proper resource handling and cleanup.
- **Callable Objects**: Create objects that can be used as functions, useful for creating flexible and reusable code.

Dunder methods allow you to make your classes interact seamlessly with Python's built-in functions and operations, providing a powerful way to extend and customize behavior in your applications.

## Class Relationships

In object-oriented programming (OOP), understanding the relationships between classes is crucial for designing effective and maintainable systems. The primary relationships include **inheritance**, **composition**, **aggregation**, and **association**. Each of these relationships has distinct characteristics and serves different purposes in object-oriented design.

### 1. Inheritance

Inheritance is a fundamental concept where a class (subclass) inherits attributes and methods from another class (superclass). This relationship is known as the **"IS-A"** relationship.

**IS-A Relationship**:

**Definition**: The subclass is a specific type of the superclass. For instance, if you have a `Vehicle` class, and `Car` inherits from `Vehicle`, then **a `Car` "IS-A" `Vehicle`.**

**Example**:

```python
class Animal:
    def speak(self):
        print("Animal speaks")

class Dog(Animal):
    def bark(self):
        print("Dog barks")

# Usage
dog = Dog()
dog.speak()  # Animal speaks
dog.bark()   # Dog barks
```

- **Benefits**: Code reusability, polymorphism, and a clear hierarchical structure.

### 2. Association

Association represents a general relationship between classes where one class uses or interacts with another. This can be a **one-to-one**, **one-to-many**, or **many-to-many** relationship.

**Association**:

**Definition**: Describes a relationship where classes collaborate but do not necessarily have a strong ownership. For instance, a `Customer` class might associate with an `Order` class.

**Example**:

```python
class Order:
    def __init__(self, order_id):
        self.order_id = order_id

class Customer:
    def __init__(self, name):
        self.name = name
        self.orders = []

    def place_order(self, order):
        self.orders.append(order)

# Usage
customer = Customer("Alice")
order1 = Order("001")
customer.place_order(order1)
```

- **Benefits**: Provides flexibility in relationships, allows objects to interact without strong dependencies.

Each relationship type in OOP—inheritance, composition, aggregation, and association—plays a crucial role in defining how classes interact and depend on one another. Understanding these relationships helps in designing robust and maintainable systems:

- **Inheritance** (IS-A): Establishes a hierarchical relationship where one class is a specialized version of another.
- **Composition** (HAS-A): Models a part-whole relationship with strong coupling.
- **Aggregation** (HAS-A): Represents a weaker coupling than composition, indicating a more flexible part-whole relationship.
- **Association**: Describes general interactions between classes with varying degrees of dependency.

These relationships provide different ways to model real-world interactions and dependencies, enabling more organized and scalable code.

### 3. Composition

Composition describes a **"HAS-A"** relationship where a class contains objects of other classes. It models a **part-whole relationship**, where one class is composed of one or more classes.

**HAS-A Relationship**:

**Definition**: The class contains instances of other classes as attributes. For example, a `Library` class might **"HAS-A"** collection of `Book` objects.

**Example**:

```python
class Book:
    def __init__(self, title):
        self.title = title

class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)

# Usage
library = Library()
book1 = Book("Python Programming")
library.add_book(book1)
```

- **Benefits**: Promotes modularity and flexibility, allows changes in one component without affecting others.

### 4. Aggregation

Aggregation is a special type of association that represents a "**HAS-A**" relationship but with weaker coupling than composition. It implies that the contained object can exist independently of the container.

**Aggregation**:

**Definition**: The relationship is more loosely bound compared to composition. For example, a `Department` class might have an aggregation relationship with a `Professor` class, where a professor can exist independently of the department.

**Example**:

```python
class Professor:
    def __init__(self, name):
        self.name = name

class Department:
    def __init__(self):
        self.professors = []

    def add_professor(self, professor):
        self.professors.append(professor)

# Usage
department = Department()
prof1 = Professor("Dr. Smith")
department.add_professor(prof1)
```

- **Benefits**: Provides flexibility, as the relationship is not as tightly coupled as in composition.



<img src="../_assets/aggregation_association_composition.png" style="zoom:50%;" />

Association, aggregation, and composition are fundamental concepts in object-oriented design that describe different types of relationships between classes. **Association** is a broad term used to represent any connection between objects of different classes. It signifies a general relationship and does not imply a strict connection between the lifecycles of the associated objects. For example, a `Customer` may be associated with an `Order`, indicating that a customer can place orders without the objects being tightly coupled in terms of their existence.

In contrast, **aggregation** and **composition** are more specific types of association that define stronger relationships with particular implications for the objects' lifecycles. **Aggregation** denotes a "whole-part" relationship where the part can exist independently of the whole. For instance, a `Department` might contain `Professor` objects, where professors can exist outside the department. **Composition**, however, represents a more rigid "whole-part" relationship where the existence of the parts is dependent on the whole. If the whole object is destroyed, the parts are also destroyed. For example, in a `Library`-`Book` relationship, books are considered part of the library and do not exist outside its context. In summary, while aggregation allows for more independent existence of parts, composition ensures a tighter, more dependent relationship between the whole and its parts. The key difference between these relationships is that composition and aggregation are specific forms of association, each defining the strength and nature of the relationship between objects.

https://algodaily.com/lessons/association-aggregation-composition-casting

