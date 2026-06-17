# 🎓 Academic Mobility & Workflow Database (Visual Prolog)

![Visual Prolog](https://img.shields.io/badge/Language-Visual_Prolog-blue.svg)
![Type](https://img.shields.io/badge/Project_Type-Logic_Programming-brightgreen.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)

## 📌 Overview
This repository contains a deep hierarchical database built entirely in **Visual Prolog**. The project models an international academic ecosystem, tracking universities, study programs, courses, and specific technical tasks (e.g., Spring Boot internships, C++ optimizations, or Machine Learning research). 

The goal of this project is to demonstrate advanced knowledge of logic programming, custom domain architecture, functor encapsulation, and state memory handling via dynamic facts (to prevent query backtracking duplicates).

---

## 🏗️ Database Architecture (15-Level Hierarchy)

Rather than building a flat structure, the database encapsulates **15 nested layers of containment** mapped strictly using custom enumerations and functors. The schema funnels down from the continental scope directly to the granular details of an individual academic task.

### The 15 Domain Levels:
1. `continent` (Custom Enum: europe, northAmerica, asia)
2. `country` (Custom Enum: romania, portugal, switzerland, etc.)
3. `region` (Name, Climate Type)
4. `city` (Name, Population)
5. `university` (Name, Foundation Year)
6. `campus` (Name, Location)
7. `faculty` (Name)
8. `department` (Name)
9. `studyProgram` (Custom Enum Level, Duration)
10. `academicYear` (Integer)
11. `semester` (Integer, Season)
12. `course` (Name, ECTS Credits)
13. `activity` (Custom Enum, Attendance Rule)
14. `evaluation` (Custom Enum, Weight Percentage)
15. `task` (Task Name, Difficulty, Language, Status)

### 💾 Dynamic Memory (Backtracking Handling)
Due to the non-deterministic nature of Prolog's `fail` predicate, a custom caching layer was implemented using `assert` and `retractAll`. This temporary dynamic memory stores previously queried higher-level nodes (like Country or City) during runtime, ensuring that the console outputs **strictly unique values** when traversing the 26 data records.

---

## 🚀 Features & Queries

The system runs a complete integration test featuring **40 distinct queries** upon execution. These queries test various logical conditions, including:
* Deep nesting parameter extraction (e.g., locating specific Software departments).
* Relational numerical filtering (e.g., `ECTS Credits > 10`, `City Population > 1,000,000`).
* Status verification (e.g., retrieving tasks marked as `inProgress` vs `completed`).
* Cross-referencing constraints (e.g., filtering universities based in Switzerland or Romania).

---

## ⚙️ How to Run

1. Clone the repository to your local machine.
2. Ensure you have the **Visual Prolog** compiler installed.
3. Keep the file directory structure intact (the code relies on `file::consult("..\\data.txt", databaseClauses)`).
4. Build and Run `main.pro`.
5. The console will sequentially execute all 40 queries, load the knowledge base, assert dynamic facts, and output the clean results.

---

*Authored by David Bonaccorsi.*
