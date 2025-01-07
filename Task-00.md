

**Task 1: Create a "CodingGita Students" database**

Create a new MongoDB database called `CodingGita`.
```js
    use codinggita
```
 Add two collections:
- `students`: Name, roll number, department, year, courses enrolled.
```js
    db.createCollection("students");
```
- `courses`: Course code, name, credits, instructor.
```js
    db.createCollection("courses");
```

Insert sample data into both collections.

```js

    db.students.insertMany([
    { 
        "name": "Jenil",
        "rollNumber": 101,
        "department": "Computer Science",
        "year": 2,
        "coursesEnrolled": ["CS101", "CS102"]
    },
    { 
        "name": "Mahir",
        "rollNumber": 102,
        "department": "Computer Science",
        "year": 2,
        "coursesEnrolled": ["CS101", "CS103"]
    },
    { 
        "name": "Arjun",
        "rollNumber": 103,
        "department": "Electrical Engineering",
        "year": 3,
        "coursesEnrolled": ["EE101", "EE102"]
    }
    ]);

    db.courses.insertMany([
    { 
        "courseCode": "CS101", 
        "courseName": "Introduction to Programming", 
        "credits": 3, 
        "instructor": "Prof. Sharma" 
    },
    { 
        "courseCode": "CS102", 
        "courseName": "Data Structures", 
        "credits": 3, 
        "instructor": "Prof. Gupta" 
    },
    { 
        "courseCode": "CS103", 
        "courseName": "Algorithms", 
        "credits": 3, 
        "instructor": "Prof. Kapoor" 
    },
    { 
        "courseCode": "EE101", 
        "courseName": "Basic Electrical Engineering", 
        "credits": 4, 
        "instructor": "Prof. Verma" 
    },
    { 
        "courseCode": "EE102", 
        "courseName": "Circuit Theory", 
        "credits": 4, 
        "instructor": "Prof. Yadav" 
    }
    ]);

```
---

**Task 2: Perform CRUD operations**
- Add a few more students and courses to the database.
```js
    db.students.insertMany([
    { 
        "name": "Dev",
        "rollNumber": 104,
        "department": "Computer Science",
        "year": 2,
        "coursesEnrolled": ["CS101", "CS102","CS103"]
    },
    { 
        "name": "Kalpan",
        "rollNumber": 105,
        "department": "Computer Science",
        "year": 2,
        "coursesEnrolled": ["CS101", "CS103","EE101"]
    },
    { 
        "name": "Dax",
        "rollNumber": 106,
        "department": "Electrical Engineering",
        "year": 3,
        "coursesEnrolled": ["EE101", "EE102","CS102"]
    }
    ]);
```
- Query data based on:
  - Department (e.g., "Computer Science").
  ```js
   db.students.find({ "department": "Electrical Engineering" });
  ```
  - Year (e.g., "2").
  ```js
   db.students.find({ "year": 3 });
  ```
  - Courses enrolled (e.g., "CS101").
  ```js
    db.students.find({ "coursesEnrolled": "CS103" });
    ```
- Update the courses for a specific student (e.g., adding a new course).
```js
    db.students.updateOne(
    { "name": "Arjun" },
    { $push: { "coursesEnrolled": "EE102" } }
    );
```
- Delete a student or course from the database.
```js
    db.students.deleteOne({ "name": "Arjun" });
```


