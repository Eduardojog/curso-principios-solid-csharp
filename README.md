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

The Open/Closed Principle (OCP) in software design states that entities should be open for extension but closed for modification.

- **Open for Extension**: Allows adding new functionality without altering existing code.
  
- **Closed for Modification**: Existing code remains stable and unchanged.

In the provided code example:
- `Employee` class serves as a base, open for extension.
- `ShowSalaryMonthly` method accepts different employee types without modification.
- New employee types can be added without altering existing code.

This approach promotes code that is flexible, maintainable, and easily extensible


** Abstract Classes in C# **

An abstract class is a class that cannot be instantiated directly, meaning you cannot create objects of it. Instead, it is designed to be used as a base class for other classes. 

In the provided code, the `Employee` class is declared as abstract:



# Liskov Substitution Principle (LSP)

The Liskov Substitution Principle (LSP) states that objects of a superclass should be replaceable with objects of its subclasses without affecting the behavior of the program.

## Example

In the provided example, we have two subclasses of the `Employee` class: `EmployeeFullTime` and `EmployeeContractor`. Each subclass overrides the `CalculateSalary` method to provide its own implementation.

- `EmployeeFullTime`: Calculates the salary based on hours worked plus extra hours.
- `EmployeeContractor`: Calculates the salary based solely on hours worked.

By adhering to the LSP, objects of any subclass (`EmployeeFullTime` or `EmployeeContractor`) can be substituted for objects of the superclass (`Employee`) without affecting the program's logic. Each subclass provides its own salary calculation method, ensuring that the behavior remains consistent across different types of employees.


You can perform salary calculations using any subclass, and the method below demonstrates this flexibility:


public static decimal CalculateTotalSalary(List<Employee> employees)
{
    decimal totalSalary = 0;
    foreach (var employee in employees)
    {
        totalSalary += employee.CalculateSalary();
    }
    return totalSalary;
}

# Interface Segregation Principle (ISP)

The Interface Segregation Principle (ISP) advocates dividing large interfaces into smaller ones. In C#, where multiple inheritance is not allowed but multiple interfaces can be implemented, ISP promotes the creation of interfaces that are focused on specific responsibilities.

```csharp
namespace InterfaceSegregation
{
    public class Developer : IWorkTeamActivities, IDevelopActivities
    {
        public Developer()
        {
        }

        public void Plan() 
        {
            throw new ArgumentException();
        }

        public void Communicate() 
        {
            throw new ArgumentException();
        }

        public void Develop() 
        {
            Console.WriteLine("I'm developing the functionalities required");
        }
    }
}
```
