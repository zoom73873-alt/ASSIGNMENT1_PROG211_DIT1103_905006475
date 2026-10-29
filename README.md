# Student Results System

A beginner Python program that creates student records, updates names and scores, and displays results. It demonstrates inheritance using two classes: `Person` and `Student`.

The records are fictional. The program uses no imports, database or file storage.

## Requirements

- Python 3 installed on your computer.
- A text editor such as VS Code or Notepad.
- No extra packages are needed.

## How to run the program

1. Save the supplied Python code as `student_results.py`.
2. Put this `README.md` in the same folder.
3. Open a terminal in that folder.
4. Run:

   ```bash
   python student_results.py
   ```

   If your computer uses the `python3` command, run:

   ```bash
   python3 student_results.py
   ```

The demonstration runs immediately. It does not ask you to type information into a menu.

## What the program does

1. Creates two `Student` objects.
2. Adds them to the `students` list.
3. Changes Alieu's name to `Alieu A. Kamara`.
4. Changes his score from `45` to `68`.
5. Displays both students and their results.
6. Displays the number of Student objects created.
7. Checks whether `105` is a valid score.

## Classes and inheritance

### Person

`Person` is the parent class. Its constructor stores a name, student ID and age.

- `update_name(new_name)` changes the name after checking that it is not blank.
- `display_info()` prints the name, student ID and age.

### Student

`Student` inherits from `Person`:

```python
class Student(Person):
```

Its constructor calls `super().__init__()` to initialise the inherited details. It then stores the course and score.

| Method | Purpose |
| --- | --- |
| `update_score(new_score)` | Checks and changes the score. |
| `get_result()` | Returns `Pass` or `Needs improvement`. |
| `display_info()` | Prints the inherited details, course, score and result. |
| `get_total_students()` | Class method that returns the number of Student objects created. |
| `is_valid_score(score)` | Static method that checks a score without requiring a Student object. |

`Student.display_info()` overrides the parent method. It calls `super().display_info()` first, then prints the extra student details.

## Managing the records

The `students` list holds the records added to the system.

- `add_student(student)` accepts a `Student` object and rejects a duplicate student ID in the list.
- `display_students()` prints the stored records or `No student records.` when the list is empty.

`Student.total_students` counts successfully constructed Student objects, not the number of records in the list. For example, creating an object with an existing ID increases the object count even if `add_student()` later rejects that duplicate.

## Validation and result rule

- Name, student ID and course must contain non-whitespace text when creating a Student.
- Leading and trailing spaces are removed from those text values.
- Age must be an integer of zero or greater.
- Score must be an `int` or `float` between `0` and `100`, inclusive. Boolean values are rejected.
- Invalid constructor or update values raise `ValueError`. The demonstration does not catch these errors.

The result rule is:

| Score | Result |
| --- | --- |
| 50 to 100 | Pass |
| Below 50 | Needs improvement |

This is a demonstration rule, not an official university grading policy.

## Expected output

Running the supplied code unchanged produces:

```text
Student added: S001
Student added: S002

--- Student result ---
Name: Alieu A. Kamara
Student ID: S001
Age: 21
Course: Python OOP
Score: 68
Result: Pass

--- Student result ---
Name: Hawa Conteh
Student ID: S002
Age: 20
Course: Networking
Score: 82
Result: Pass

Total Student objects created: 2
Is 105 a valid score? False
```

## Try adding another student

Place these lines after the two existing `add_student()` calls and before `display_students()`:

student3 = Student("Mariama Sesay", "S003", 19, "Cyber Security", 76)


To change that student's score, use:



Run the file again to see the changes. To keep validation in place, use the update methods when changing names or scores.

## Limitations

- Records exist only in memory and are lost when the program ends.
- Running the file again recreates the demonstration records from the code.
- The program has no interactive menu, login, search or delete feature.
- Duplicate IDs are checked when adding to the list, not during object construction.
- Text arguments are expected to be strings; the program does not validate every possible argument type.
