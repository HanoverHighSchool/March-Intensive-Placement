# Introduction

The March Intensive Placement (MIP) program is intended to act as a replacement for the current registration and placement systems in place. It seeks to meet or exceed the functional capabilities of previous MIP systems.

# Functionality Requirements

- Ability to import pre-existing student lists (_[read more](#import)_)
- Replaces the [March Intensive Website](http://sites.hanovernorwichschools.org/hhs-march-intensive/)
 - Home Page with MI description (_[read more](#home-page-go-back)_)
 - Course List (_[read more](#course-list-go-back)_)
 - MI Calendar (over the entire year) (_[read more](#mi-calendar-go-back)_)
 - MI Schedule (over a given MI day) (_[read more](#mi-schedule-go-back)_)
 - Grades and Evaluation info page (_[read more](#grades-and-evaluation-go-back)_)
 - Placement process info page (_[read more](#placement-process-go-back)_)
 - Forms (paperwork) page (_[read more](#forms--paperwork-go-back)_)
 - Thank you page (_[read more](#thank-you-go-back)_)
 - Ability to manage who can edit the website (_[read more](#admin-management)_)
- Replaces the [March Intensive Registration Form](http://sites.hanovernorwichschools.org/hhs-march-intensive/home/registration) (_[read more](#registration-page)_)
- Replaces the manual placement process (_[read more](#placement-process)_)

## Static Pages

### Home Page (_[go back](#functionality-requirements)_)

This page serves as a landing page for the website. If someone goes to the website, this is the first thing they will see. Aside from a site-wide nav-bar, it may have larger links to specific items to allow for faster navigation.

### Course List (_[go back](#functionality-requirements)_)

This has the course list and descriptions for each course. Administration can easily edit this list using the Django Admin panel. The list is dynamically generated and can be filtered by course type.

Clicking on a course brings you to the course page, which shows the same information as on the course list, however it may show more information in the future.

### MI Calendar (_[go back](#functionality-requirements)_)

This shows the year-long calendar for the MI process. This is not a calendar for the MI week.

### MI Schedule (_[go back](#functionality-requirements)_)

This explains the schedule on a given MI day. However it does not include exceptions for classes meeting at odd times.

### Grades and Evaluation (_[go back](#functionality-requirements)_)

This explains how students are graded and evaluated on their MI participation.

### Placement Process (_[go back](#functionality-requirements)_)

This explains how students are placed. This information concerns the [placement process](#placement-process) detailed below.

### Forms / Paperwork (_[go back](#functionality-requirements)_)

This page has downloads for the forms and paperwork that various classes may require.

### Thank You (_[go back](#functionality-requirements)_)

Thanking people in the community

## Registration Page

- Enter name (or ID) to identify student with entry in pre-filled database
- Enter Hartford Tech and Ford Sayre status
- Select desired classes

## Placement Process

The system has a student list, class list, and request set as supplied data.

### From the [March Intensive Website](http://sites.hanovernorwichschools.org/hhs-march-intensive/home/mi-placement)

> Seniors will receive priority in placement. All seniors will be numbered. A random number generator will select a number and the senior with that number will be given his or her first choice. This process will continue until all seniors have been placed, using the senior’s list of preferences as course enrollments fill up. The same procedure will be followed for each succeeding class. If a student’s first choice is already filled, the placement will continue as if the student’s second choice were actually the first, etc. In an effort to ensure underclassmen receive one of their top choices, they will be signing up for courses a week after upperclassmen, selecting from an updated list of available courses.

> The placement procedure is obviously weighted to benefit upperclassmen with the understanding that all students will benefit from the procedure at some time in their high school careers. We also feel that it is very important to have the March Intensive support of the older students, who set the tone and direction for the student body.

### Code Flow

```javascript
var students = [Student, Student, Student(...)]
var courses = [Course, Course, Course(...)]
for student in students {
    for request in student {
        try to place student
        if success {
            break
        } else {
            continue
        }
    }
}
```

## Import

YAY IMPORT

## Admin Management

Account management for administrators is done through the Django account system. Any user with access can add more users with varying levels of privilege. For example, one might create an account (through the website) for a teacher who is part of the March Intensive group. They would then get permissions allocated to them, and would be able to manage the website from their own login.

# Running the System

1. The first step is to set up the system. At this time it is undecided wether set up will be brand new or will be reconfiguring the previous year's website.
2. After the server is running, course and student data must be entered. Student data will (most likely) be imported from an external data source). Course data will most likely be manually entered.
3. When the website goes "live" students and parents will be able to browse it as a replacement to the current website.
4. After students have a mental list, when registrations are open, students will complete the signup process.
 - It is unknown at this time how this process will be kept secure. Current setups have no security implementations or duplicate preventions.
 - Duplicate submissions, and submissions for names that don't exist, will most likely be prevented. It is most likely that students wishing to modify their submission will need to request that ability.
 - Currently seniors and juniors sign up first, then Sophomores and Freshmen. Because student data includes grades, step 4 will be able to restrict who can sign up when.
5. At some point in time, it will be decided to close registration for Seniors and Juniors. The administrator would at this point see who has no signed up and would be able to
 - Manually fill in requests for that student
 - Ignore that student (for the time being)
 - Go to the student's page, so as to modify or delete the student
6. At any point in time, a course roster can be generated. After step 5, the rosters for grades 11 and 12 will be complete.
 - Privacy requirements will be decided at a later date.
 - The rosters will be in an easy to print format.
7. Repeat step 4 and 5 for Sophomores and Freshmen
8. Generate rosters and notify students via email of their course selections
9. Shut down the system
 - At this time it is not known wether the system will be preserved from year to year. At this time the most likely course of action will be a completely new install each year.