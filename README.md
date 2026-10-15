# Smart University Management System

A Core Java mini project that models a university's people — **Students**, **Faculty**, and **Staff** — as one connected object-oriented system. Built to practice the core OOP pillars in a single, realistic domain rather than as isolated exercises.

## Class Hierarchy

```
                Person (abstract)
               /       |        \
          Student   Faculty    Staff
                        |         |
                    Payable   Payable
                        |
                  Identifiable

          Department (supporting class, holds Faculty)
```

## OOP Concepts Covered

| Concept | Where it appears |
|---|---|
| Encapsulation | Private fields with getters/setters in every class |
| Abstraction | `Person` abstract class; abstract `calculateRole()` |
| Inheritance | `Student`, `Faculty`, `Staff` extend `Person` |
| Interface (single) | `Staff implements Payable` |
| Interface (multiple) | `Faculty implements Payable, Identifiable` |
| Runtime polymorphism (overriding) | `calculateRole()`, `displayDetails()`, `toString()` differ per class |
| Compile-time polymorphism (overloading) | `calculateSalary()` in Faculty/Staff, `addFaculty()` in Department |
| `super()` | Every child constructor calls `Person`'s constructor |
| `this()` constructor chaining | `Person()` → `Person(name, age)`; `Student(name, age, course)` → `Student(name, age, course, semester)` |
| Static members | `totalPersonsCreated`, `generateId()`, `totalDepartments` |
| `final` | `UNIVERSITY_NAME` |
| `Object` class override | `toString()` in `Person`, inherited/reused by every subclass |
| Automated ID generation | IDs are generated internally via a static counter — never entered manually |

## Design Notes

- **`Student` does not implement `Payable`** — students don't earn a salary, so forcing the interface onto them would be meaningless.
- **`Faculty` implements two interfaces at once** (`Payable` and `Identifiable`) — something a single abstract class can't do on its own. This is the core argument for interfaces over deeper inheritance chains.
- **`Staff` does not implement `Identifiable`** — a deliberate design choice reflecting that staff in this system don't carry the same ID-card access as faculty.

## Project Structure

```
src/com/overallOOP/
├── Person.java
├── Student.java
├── Faculty.java
├── Staff.java
├── Department.java
├── Payable.java
├── Identifiable.java
└── SmartUniversityManagementSystem.java   (entry point)
```

## How to Compile & Run

```bash
cd src
javac com/overallOOP/*.java
java com.overallOOP.SmartUniversityManagementSystem
```

## Sample Output

```
Creating objects...
Student[ ID = 101 Name Amruta Age = 23 Role = Student University Name = SPPU University], course = Computer Science, semester = 1

Student[ ID = 102 Name Shravani Age = 33 Role = Student University Name = SPPU University], course = Entc, semester = 5

Faculty[ ID = 103 Name Aarya Age = 22 Role = Faculty University Name = SPPU University]
Faculty salary (no bonus): 45000.0
Faculty salary (with bonus): 50000.0
Faculty2 salary (with bonus): 7000.0
Staff salary (base): 48000.0
Faculty ID Card Generated for Aarya (ID: FAC-103)
Aarya added to Computer Science department.
Kaveri added to Computer Science department. Note: Head of Department
Faculty in Computer Science:
 - Aarya
 - Kaveri
Total persons created: 5
Total departments: 1
```

## Tech

- Java (Core Java, no external libraries or frameworks)

---

Built as a hands-on OOP mini project — feedback welcome!
              
