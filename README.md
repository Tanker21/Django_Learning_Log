#Django framework project: Learning Log

##Summary##
This is a project from the book, Python Crash Course, by Eric Matthes. It is a Django project for creating logs on what users have learned, and allows users register new users, log out, see only their own topics and entries, and is public facing (through the use of Heroku).

##Purpose##
This project teaches the fundamental components of the django framework, how to manage users and user permissions, a bit on security, and offers a way to get a website to be public facing.  There is also coverage on how to use git for version control.

##Django components##
Django is a web framework for Python that simplifies setting up and managing websites.  This project contains users, and their authentication/authorization configurations, a database to store user and entry items, topics users could create, and entries related to those topics as objects.  

###Django-model, view, and templates###
Django handles these topic and entry objects in sections called models, views, and templates (with intermediate url patterning).  The model are the classes of these objects, detailing their schema and methods.  The views are the way in which Django knows how to handle requests about these objects, whether it is displaying, filtering, applying restriction/permissions, or displaying forms for adding or editing these objects.  The templates are the webpage frameworks on what and how to display data to the end user.  The urls for these pages are patterned and dictate which of these templates needs to be displayed.  So the workflow in Django is to accept a request from the client (a click on a button or link in the webpage), look for that url pattern, pull up the associated view, and call the assigned web page template, handing in data as needed.

###Models###
The models this project used were:
-Topic (a short header of a learned item)
-Entry(a lengthier description of the learned item).  

###Views###
The views were all that the user was allowed to perform: 
-topics (display a list of all topics the current user has created)
-topic (a detailed look at a single topic and all related entries for that topic),
-new_topic (creating a new topic)
-new_entry (creating a new entry for a certain topic)
-edit_topic (editing an existing topic), edit_entry (editing an existing entry for a certain topic)
-home page-shows a banner of the project, who is logged in, a link to topics, and a logout link

###Templates###
There were templates and urls for each of these views, as well as Registering a new user, user login and logout, and error handling (404 and 500 errors).

##Authentication, authorization, security, and error handling##
Authentication was handled by setting @login_required decorators on all the views to restrict access to only logged in users, which was checked in the project’s SQL database.  Passwords are hashed and not stored directly from a user’s registration.  

Authorization came in the form that users could only see their own topics and entries, not any other user’s topics and entries, and was handled by a check of the topics in the database to the currently logged in user (entries are related to topics and so basically inherit this property indirectly).

Security and errors were handled by custom handling of 404 and 500 web errors (with their own web templates) which further enforced authorization (a manually manipulated url, such as adding a 1 after ‘topics’ to try and force the first topic in the database to display, was checked against the current user, and if not authorized was shown a 404 page not found error).

##Git and application version control##
The book Python Crash Course also showed how to integrate git to add version control to the project, which was also used in pushing the app to Heroku.  Version control allows for versioning of a project so that milestones of functioning applications can be made, and  branches off that functioning application can be made to modify and add new functionality, and tested, isolated from the main branch, and then once working, merged into the main code, and pushed into production.  This version control can also be utilized with teams of developers, as different people can branch off the main source code and work independently and then merge code back to the main, and git can handle the changes and any collisions (code modified by two or more people).  

##Python virtual environment##
The book also worked with setting up Python virtual environments.  Python allows you to create isolated environments that allow you to install certain packages with their own versions, that work for the specific project, that may conflict with other projects if they happen to use different versions or have different dependencies.  These virtual environments also allow for the documentation of what is required for this specific environment (a ‘requirements.txt’ file notating all the packages imported and their specific versions) and allow for the installation of these packages in order to set up the exact environment on another developer’s local system (or in this case, the Heroku server side).

This project comes out of the book **Python Crash Course** by [Eric Matthes](https://github.com/ehmatthes).  Thanks Eric for assisting me through my many typos and issues in completing this project!
