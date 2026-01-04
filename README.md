# University Course Registration System (UCRS)
## Group 06 – Software Engineering Project

---

## 📌 Project Overview

The **University Course Registration System (UCRS)** is a web-based information system designed to manage student course enrollment, scheduling, and academic records within a university or college environment. The system enables students to browse available courses, register for classes, drop or swap courses, and view academic schedules and grades. The registrar's office verifies prerequisites, manages course capacities, and oversees registration timelines. Instructors can upload grades, manage course rosters, and post announcements.

This project focuses on **system analysis and design** using UML modeling techniques, including context models, activity diagrams, use case diagrams, and sequence diagrams.

---

## 🎯 System Actors

- **Student**: Browse courses, register/drop courses, view schedules and grades
- **Academic Advisor**: Review and approve course enrollment requests
- **Instructor**: View class lists, manage grades, post announcements
- **Administrator**: Manage courses, users, schedules, and system configurations

---

## 🔗 External Systems

- **University Database**: Stores and retrieves student, course, enrollment, and grade data
- **Payment System**: Processes tuition and fee payments for course registrations

---

## 📁 Repository Structure

```
uml/
│
├── README.md                    # This file
│
├── docs/
│   ├── report.md                # Main Markdown report (to be converted to PDF)
│   └── report.pdf               # Generated PDF report (via Pandoc)
│
└── uml/
    ├── context_ucrs.puml                    # Context model diagram
    ├── activity_student_register.puml       # Student registration activity diagram
    ├── activity_admin_course_mgmt.puml      # Admin course management activity diagram
    ├── student_composite_usecase.puml       # Composite use case for Student actor
    ├── usecase_register_course.puml         # Individual use case: Register Course
    ├── usecase_drop_course.puml             # Individual use case: Drop Course
    ├── seq_register_stakeholder.puml        # Sequence: Register Course (Stakeholder view)
    ├── seq_register_developer.puml           # Sequence: Register Course (Developer view)
    ├── seq_dop_stakeholder.puml              # Sequence: Drop Course (Stakeholder view)
    └── seq_drop_developer.puml               # Sequence: Drop Course (Developer view)
```

---

## 📊 Diagrams Included

### Part I: Context and Activities

1. **Context Model** (`context_ucrs.puml`)
   - Illustrates where UCRS fits within the overall business environment
   - Shows interactions with external actors (Student, Advisor, Instructor, Administrator) and external systems (University Database, Payment System)

2. **Activity Diagram – Student Course Registration** (`activity_student_register.puml`)
   - Represents the workflow for student course registration
   - Includes prerequisite validation, seat availability checks, and advisor approval process
   - Shows alternative flows for rejection scenarios

3. **Activity Diagram – Administrator Course Management** (`activity_admin_course_mgmt.puml`)
   - Describes the process for administrators to create, update, or delete courses
   - Includes setting schedules and capacity, and updating the database

### Part II: Use Cases and Interactions

4. **Composite Use Case Diagram – Student** (`student_composite_usecase.puml`)
   - Shows all use cases involving the Student actor
   - Includes: Browse Courses, Register Course, Drop Course, View Schedule, View Grades

5. **Individual Use Case – Register Course** (`usecase_register_course.puml`)
   - Detailed use case diagram identifying all interacting actors
   - Actors: Student, Academic Advisor, University Database, Payment System

6. **Individual Use Case – Drop Course** (`usecase_drop_course.puml`)
   - Detailed use case diagram identifying all interacting actors
   - Actors: Student, Academic Advisor, University Database, Payment System

7. **Sequence Diagram – Register Course (Stakeholder View)** (`seq_register_stakeholder.puml`)
   - High-level sequence diagram for stakeholders
   - Focuses on business interactions without technical details

8. **Sequence Diagram – Register Course (Developer View)** (`seq_register_developer.puml`)
   - Detailed sequence diagram for developers
   - Includes technical components, services, and database interactions

9. **Sequence Diagram – Drop Course (Stakeholder View)** (`seq_dop_stakeholder.puml`)
   - High-level sequence diagram for stakeholders
   - Shows business-level interactions for dropping a course

10. **Sequence Diagram – Drop Course (Developer View)** (`seq_drop_developer.puml`)
    - Detailed sequence diagram for developers
    - Includes enrollment service, database operations, and refund processing

---

## 🛠 Tools & Technologies

- **Visual Studio Code (VSC)**: Primary IDE for development
- **PlantUML Extension**: For creating and viewing UML diagrams
- **Draw.io**: Alternative tool for diagram creation (optional)
- **Pandoc**: For converting Markdown to PDF
- **Git & GitHub**: Version control and collaboration

---

## 📝 Use Case Descriptions

The report includes comprehensive tabular descriptions for:
- **Register Course**: Goals, preconditions, postconditions, main scenario, and alternate flows
- **Drop Course**: Goals, preconditions, postconditions, main scenario, and alternate flows

These descriptions are included in `docs/report.md` in Section 4.3.

---

## 🚀 Getting Started

### Prerequisites

1. **Visual Studio Code** with PlantUML extension installed
   - Install the "PlantUML" extension by jebbs
   - Or use Draw.io integration

2. **Pandoc** (for PDF generation)
   - Download from: https://pandoc.org/installing.html
   - Verify installation: `pandoc --version`

### Viewing Diagrams

1. Open any `.puml` file in VS Code
2. Use the PlantUML preview (right-click → "Preview PlantUML" or use the command palette)
3. Diagrams will render automatically in the preview pane

### Generating the PDF Report

1. Navigate to the project root directory:
   ```powershell
   cd C:\Users\WinDows\Desktop\uml
   ```

2. Convert Markdown to PDF using Pandoc:
   ```powershell
   pandoc docs/report.md -o docs/report.pdf
   ```

3. If your instructor requires a specific filename (e.g., `se_report_group_06.pdf`):
   ```powershell
   pandoc docs/report.md -o docs/se_report_group_06.pdf
   ```

### Viewing the Report

- **Markdown**: Open `docs/report.md` in VS Code with Markdown preview
- **PDF**: Open `docs/report.pdf` in any PDF viewer

---

## 📋 Assignment Deliverables Checklist

- ✅ `/docs/report.md` - Markdown report with embedded PlantUML diagrams
- ✅ `/docs/report.pdf` - PDF version of the report (generated via Pandoc)
- ✅ `/uml/*.puml` - All PlantUML source files for diagrams
- ✅ `README.md` - Project documentation (this file)

---

## 👥 Team Collaboration

- Each team member must push their own commits regularly
- Commits will be used as evidence of participation
- Maintain clear commit messages describing changes

---

## 📌 Notes

- This project focuses on **analysis and design**, not full system implementation
- All diagrams are created using PlantUML syntax and embedded directly in the Markdown report
- The final PDF report must be submitted to the E-Learning portal
- Ensure all PlantUML diagrams render correctly before generating the PDF

---

## 🔍 Quick Reference

- **Report Location**: `docs/report.md`
- **UML Diagrams**: `uml/*.puml`
- **Primary Actor**: Student
- **Selected Use Cases**: Register Course, Drop Course
- **Diagram Types**: Context Model, Activity Diagrams, Use Case Diagrams, Sequence Diagrams

---

## 📞 Support

For issues with:
- **PlantUML rendering**: Check VS Code extension installation
- **PDF generation**: Verify Pandoc installation and path
- **Diagram syntax**: Refer to PlantUML documentation at http://plantuml.com/

---

**Last Updated**: December 2024  
**Group**: 06  
**Course**: Software Engineering – System Analysis and Design

