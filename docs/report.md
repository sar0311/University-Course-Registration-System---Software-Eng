% Group 06 – University Course Registration System
% Software Engineering – System Analysis and Design Report

# 1. Introduction

The **University Course Registration System (UCRS)** is a web-based information system that supports student course enrollment, scheduling, and academic records management.  
This report documents the analysis and design of UCRS using UML models, focusing on how the system interacts with its environment and how key business processes are realized.

# 2. System Overview

UCRS allows **students** to browse courses, register and drop courses, and view their schedules and grades.  
**Academic advisors** review and approve certain enrollment requests, **instructors** manage class lists and grades, and **administrators** configure courses, users, and schedules.  
The system integrates with a **university database** for persistent storage and a **payment system** for processing tuition and fee payments.

# 3. Part I – Context and Activities

## 3.1 Context Model

The context diagram shows UCRS at the center of the academic environment, interacting with both human actors and external systems.

```plantuml
@startuml
!include ../uml/context_ucrs.puml
@enduml
```

## 3.2 Activity Diagram – Student Course Registration

This activity diagram represents the high-level workflow a student follows to register for a course, including prerequisite and capacity checks and advisor approval.

```plantuml
@startuml
!include ../uml/activity_student_register.puml
@enduml
```

## 3.3 Activity Diagram – Administrator Course Management

This activity diagram describes how an administrator manages course offerings, including creating or updating courses, configuring schedules, and updating the database.

```plantuml
@startuml
!include ../uml/activity_admin_course_mgmt.puml
@enduml
```

# 4. Part II – Use Cases and Interactions

## 4.1 Composite Use Case – Student

The composite use case diagram below shows all major interactions the **Student** actor has with UCRS.

```plantuml
@startuml
!include ../uml/student_composite_usecase.puml
@enduml
```

## 4.2 Individual Use Case – Register for Course

### 4.2.1 Use Case Diagram

```plantuml
@startuml
!include ../uml/usecase_register_course.puml
@enduml
```

### 4.2.2 Use Case Description (Register for Course)

| Field           | Description                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------|
| Use Case Name   | Register for Course                                                                             |
| Primary Actor   | Student                                                                                         |
| Supporting Actors | Academic Advisor, Payment System, University Database                                        |
| Goal            | Allow a student to enroll in a course that satisfies prerequisites and capacity constraints.   |
| Preconditions   | Student is authenticated; registration period is open; student has no blocking holds.          |
| Postconditions  | Enrollment record is created or updated; student schedule is updated; payment is recorded if required. |

**Main Scenario**

| Step | Actor/System        | Description                                                                          |
|------|---------------------|--------------------------------------------------------------------------------------|
| 1    | Student             | Logs into UCRS and navigates to the course registration page.                      |
| 2    | System              | Displays available courses and search/filter options.                               |
| 3    | Student             | Searches and selects a course to register for.                                      |
| 4    | System              | Retrieves course details and validates prerequisites and schedule conflicts.        |
| 5    | System              | Checks seat availability and registration policies.                                 |
| 6    | System              | If required, sends the enrollment request to the Academic Advisor for approval.     |
| 7    | Academic Advisor    | Reviews the request and approves or rejects it.                                     |
| 8    | System              | If approved, requests payment from the Payment System (if applicable).              |
| 9    | Payment System      | Processes payment and returns success or failure.                                    |
| 10   | System              | Creates or updates the enrollment record in the University Database.                |
| 11   | System              | Updates the student’s class schedule.                                               |
| 12   | System              | Shows a confirmation message and registration status to the student.                |

**Alternate / Exceptional Flows**

- **A1 – Prerequisites Not Met**: At Step 4, if prerequisites are not satisfied, the system rejects the request and shows an explanatory message.  
- **A2 – No Seats Available**: At Step 5, if no seats are available, the system informs the student that the course is full and may offer a waitlist option.  
- **A3 – Advisor Rejects Request**: At Step 7, if the advisor rejects the request, the system notifies the student with the rejection reason.  
- **A4 – Payment Failure**: At Step 9, if payment fails, the system marks the registration as pending or cancelled and prompts the student to retry payment.

## 4.3 Individual Use Case – Drop Course

### 4.3.1 Use Case Diagram

```plantuml
@startuml
!include ../uml/usecase_drop_course.puml
@enduml
```

### 4.3.2 Use Case Description (Drop Course)

| Field           | Description                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------------------|
| Use Case Name   | Drop Course                                                                                           |
| Primary Actor   | Student                                                                                               |
| Supporting Actors | Academic Advisor, Payment/Refund Service, University Database                                      |
| Goal            | Allow a student to drop an enrolled course in accordance with academic and financial policies.       |
| Preconditions   | Student is authenticated; course is currently enrolled; drop period/policy allows dropping.          |
| Postconditions  | Enrollment record is updated (status = DROPPED); refund is issued or recorded if eligible.          |

**Main Scenario**

| Step | Actor/System        | Description                                                                             |
|------|---------------------|-----------------------------------------------------------------------------------------|
| 1    | Student             | Logs into UCRS and navigates to their current course schedule.                         |
| 2    | System              | Displays the list of enrolled courses.                                                 |
| 3    | Student             | Selects a course and requests to drop it.                                              |
| 4    | System              | Checks academic and financial policies (drop deadline, minimum load, holds, etc.).     |
| 5    | System              | If required, sends a drop request to the Academic Advisor for review.                  |
| 6    | Academic Advisor    | Approves or rejects the drop request.                                                  |
| 7    | System              | If approved and eligible, sends a refund request to the Payment/Refund Service.        |
| 8    | Payment/Refund Service | Processes any applicable refund and returns the result.                              |
| 9    | System              | Updates the enrollment record in the University Database to status = DROPPED.          |
| 10   | System              | Updates the student’s schedule and any related course capacity counts.                 |
| 11   | System              | Displays a confirmation message and any refund information to the student.             |

**Alternate / Exceptional Flows**

- **B1 – Not Eligible to Drop**: At Step 4, if policies prevent dropping (e.g., deadline passed), the system rejects the request and explains why.  
- **B2 – Advisor Rejects Request**: At Step 6, if the advisor rejects the request, the system notifies the student and leaves enrollment unchanged.  
- **B3 – Refund Not Eligible**: At Step 7–8, the refund service reports that no refund is due; the system still drops the course but indicates no refund.  

# 5. Sequence Diagrams

## 5.1 Register for Course – Stakeholder View

```plantuml
@startuml
!include ../uml/seq_register_stakeholder.puml
@enduml
```

## 5.2 Register for Course – Developer View

```plantuml
@startuml
!include ../uml/seq_register_developer.puml
@enduml
```

## 5.3 Drop Course – Stakeholder View

```plantuml
@startuml
!include ../uml/seq_dop_stakeholder.puml
@enduml
```

## 5.4 Drop Course – Developer View

```plantuml
@startuml
!include ../uml/seq_drop_developer.puml
@enduml
```

# 6. Diagrams Included

- **Context Model**: Shows UCRS and its interactions with students, staff, and external systems (database, payment).  
- **Activity – Student Course Registration**: Captures the step-by-step registration process including prerequisites, capacity, and advisor approval.  
- **Activity – Administrator Course Management**: Describes how administrators maintain course offerings and schedules.  
- **Composite Use Case – Student**: Summarizes all major services provided to the student actor.  
- **Use Case – Register for Course / Drop Course**: Provide detailed views of the primary registration and drop workflows.  
- **Sequence Diagrams**: Show the dynamic interactions among actors, services, and the database for register and drop use cases (both stakeholder and developer views).

# 7. Part III – Structural Modeling 

### Overview
Part III presents the structural design of the University Course Registration System, describing the main domain entities and the service-level architecture that supports the system’s behavior.

### 7.1 Domain Class Model
```plantuml
@startuml
!include ../uml/class_domain_model.puml
@enduml
```

### 7.2 Service Architecture Class Diagram
```plantuml
@startuml
!include ../uml/class_service_architecture.puml
@enduml
```

