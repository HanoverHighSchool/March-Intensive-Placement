## Server Side

The server is written in Python using Django

### Models
```python
Course:
	String[36] course_id
	String display_name
	String(FULL,AM,PM) course_type
	Integer max_students
	Bool is_travel
	Float cost
	ManyToManyField(Instructor) instructors
	Bool is_full
	Array student_list
	String course_time_string
	Bool paid
	String get_cost_string
```
```python
Instructor
	String[36] instructor_id
	String name
```
```python
Student
	String[36] student_id
	String first_name
	String last_name
	Integer grade
	String(NO, YES) ford_sayre'Yes')],default='NO')
	String(NO, AM, PM) hartford_tech
	Bool should_ignore
	String full_name
	Bool has_course
	Bool has_requests
	Integer number_of_requests
	JSON son_representation

	Meta: unique_together = first_name, last_name
```
```python
Request
	ForeignKey(People.Student) student
	ForeignKey(Courses.Course) course
	Integer request_rank
	Date created_at
```
```python
Placement
	ForeignKey(People.Student) student
	ForeignKey(Courses.Course) course
	Date created_at
```
### Endpoints

#### `/`, App: `Index`

- `/` Home page for students and staff
- `/?panic=panic` Help page for staff

#### `/admin`, App: `admin`

- Uses built in `django` admin panel for staff

#### `/courses`, App: `Courses`

- `/courses/` Course list for students and staff
- `/courses/<course id>/` Single course description for students and staff

#### `/register`, App: `Registrations`

- `/register/` Registration form for students
- `/register/success/` Confirmation of registration page for students

#### `/placement`, App: `Placement`

- `/placement/` Placement main page for staff
- `/placement/verify/` Verification page to fill in missing students etc.
- `/placement/process/` Page to do placements, no html sent to browser for this
- `/placement/specific-student/` Page to manage individual students and their courses
- `/placement/view/` Place to see who is enrolled in what, for staff

#### `/api`, App: `api`

- `/api/reset_placements` Reset placements
- `/api/students/incomplete` Get an incomplete student list
- `/api/students` Get a student list
- `/api/student/<student id>/ignore/true` Set the ignored status to true
- `/api/student/<student id>/ignore/false` Set the ignored status to false
- `/api/student/<student id>/ignore` Get the ignored-status of the student
- `/api/student/<student id>/reset/placements` Reset the student's placements
- `/api/student/<student id>` Get a JSON representation of the student

### Classes

### Deployment information can be found [here](https://github.com/ezfe/March-Intensive-Placement/wiki/Deployment).