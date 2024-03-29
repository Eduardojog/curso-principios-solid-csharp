# Single Responsibility Principle (SRP) in C#

## Overview
The Single Responsibility Principle (SRP) is one of the SOLID principles of software design proposed by Robert C. Martin. 

SRP states that a class should have only one reason to change, meaning it should have a single responsibility. This implies that a class should be encapsulated with only one responsibility or reason for change. If a class has more than one responsibility, it becomes harder to understand, maintain, and reuse, leading to code that is more error-prone and less flexible.

In essence, SRP promotes code cohesion and modularity by dividing responsibilities into smaller, specialized classes, making it easier to understand and maintain the codebase.

## Example
In the context of a C# application, consider the following scenario:

Suppose there's a `StudentRepository` class that contains a method called `ExportStudents` responsible for exporting students. This violates the single responsibility principle because the `StudentRepository` class now has two reasons to change: when the data access logic changes and when the export logic changes.

To adhere to SRP, the export functionality can be extracted into a separate `ExportHelper` class. This way, the `StudentRepository` class is responsible only for data access, while the `ExportHelper` class handles the export functionality, ensuring each class has a single responsibility.



# Open/Closed Principle (OCP)

The code demonstrates the Open/Closed Principle by using inheritance.

- The `Employee` class is open for extension (i.e., new types of employees can be added by creating new subclasses), 
  but closed for modification (i.e., existing code does not need to be modified to accommodate new types of employees).
  
- When calling the `ShowSalaryMonthly` method, it accepts a list of `Employee` objects, which can include different types of employees,
  such as `EmployeeFullTime` and `EmployeePartTime`. The method iterates over the list and calls the `CalculateSalaryMonthly` method,
  which is polymorphically overridden by each subclass to calculate the monthly salary based on their specific logic.

This approach avoids adding conditional logic for each employee type (e.g., using multiple `if` or `else if` statements), 
which would violate the Single Responsibility Principle (SRP) and lead to code that is not prepared for extension.


# Abstract Classes in C#

An abstract class is a class that cannot be instantiated directly, meaning you cannot create objects of it. Instead, it is designed to be used as a base class for other classes. 

In the provided code, the `Employee` class is declared as abstract:

