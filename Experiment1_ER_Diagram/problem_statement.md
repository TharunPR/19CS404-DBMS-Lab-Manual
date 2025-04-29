# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - THARUN P R

## Scenario Chosen:

University 

## ER Diagram:

![ERD_DBMS_page-0001](https://github.com/user-attachments/assets/153a0b87-0d3e-49ba-a1aa-280637bcc7d0)

## Entities and Attributes:

- **DEPARTMENT**:  
  - department_id  
  - department_name  
  - hod  
  - curriculum  
  - no. of students  
  - no. of faculties  

- **COURSE**:  
  - course_id  
  - course_name  
  - pre-requisite  
  - course_type  
  - no. of credits  
  - offered_department  

- **INSTRUCTOR**:  
  - instructor_id  
  - instructor_name  
  - department  
  - email  
  - experience  
  - designation  

- **STUDENT**:  
  - name  
  - reg no  
  - email  
  - department  
  - batch  
  - dob  
  - age
 
## Relationships and Constraints:

- **Teaches** (1:N, Total Participation)  
- **BelongsTo** (1:N, Total Participation)  
- **Offers** (1:N, Total Participation)  
- **Enrolls** (M:N, Partial Participation)  

## Extension (Prerequisite / Billing):
- **Prerequisite**:  
  - In the **COURSE** table, the **pre-requisite** attribute is used to store the **course_id** of the course that must be completed before enrolling in the current course. This creates a self-referential relationship within the **COURSE** table.

## Design Choices:

- **Brief Explanation**:  
  - **Entities**: The entities were chosen to represent the core components of an academic system: **Department**, **Course**, **Instructor**, and **Student**.
  - **Relationships**: The relationships were based on common academic structures where:
    - **Instructors** teach **Courses**.
    - **Departments** have **Instructors** and **Courses**.
    - **Students** enroll in **Courses**.
  - **Assumptions**: Each **Instructor** belongs to one **Department**, and each **Course** is offered by one **Department**. A **Student** can enroll in multiple **Courses**.
    
## RESULT

Hence, the experiment was successfully conducted by modeling an academic system with ER diagrams, capturing relationships between departments, instructors, courses, and students.
