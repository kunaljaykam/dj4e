DIY: Hello World / Sessions
===========================

In this assignment, you will make two new applications in your `django_projects`
to make it so that the `/` path actually returns a page and add a bit of code
to make use of sessions.

A key element of this assignment is that we will tell you "what to do" and
less exact steps to cut and paste.  It is time for you to understand how to "Do It Yourself" (DIY).

This assignment will not have any models - just views.  In this assignment you will
be looking at the `dj4e-samples` code and figuring out how to read and adapt sample code.
You should make sure to get the latest updates by doing the following:

    cd ~/dj4e-samples
    git pull

Be very careful pulling code from `dj4e-samples` - it often has much more
code than your program needs - so know what you are looking at before you copy
code into your application.

Building a Main Page
--------------------

It is time for the "/" in your application URL to actually refer to a real page instead
of throwing a "404 Not Found" error.  We will store this page (and other project-wide
bits) in an application named "home".  To get started:

    workon django3                  # as needed
    cd ~/django_projects/mysite
    python3 manage.py startapp home

Create an HTML file in `~/django_projects/mysite/home/templates/home/main.html` with the following HTML:

    <ul>
    <li><p><a href="/polls">A Polls Application</a></p></li>
    </ul>


You can add more HTML - but this list and links should be somewhere in the template.

Edit the file `~/django_projects/mysite/mysite/urls.py` and add following path route:

    path('', TemplateView.as_view(template_name='home/main.html')),

You will need to make sure to add the proper python imports at the top of the file to make this work.
There are lots of examples of the use of TemplateView in the `urls.py` files in `dj4e-samples`
and in the lecture materials.  Figuring out exactly how to change your `urls.py` is one of the
DIY aspects of this assignment.

Then edit the file `~/django_projects/mysite/mysite/settings.py` and add a line to load the `home`
application.  Simply duplicate the line in `INSTALLED_APPS` for the `polls` application and edit it
to reference `home` and follow the pattern of case from the `polls` line.

Make sure to run:

    python3 manage.py check

To see if your changes have syntax errors, then Reload your web application and
navigate to the top level path (i.e. no path).  You should no longer
get a "404" and instead be able to navigate to the polls application by clicking on the link.
Congratulations!  You now have a web site that is not broken.

Note that this page is not present on the <a href="https://djtutorial.dj4e.com/" target="_blank">
https://djtutorial.dj4e.com/</a> server.  It still shows "404" when you navigate to the top URL.

Playing With Sessions (DIY)
---------------------------

Your next goal is to make a new application named `hello`.  It will work like:
<a href="https://djtutorial.dj4e.com/hello" target="_blank">
https://djtutorial.dj4e.com/hello</a>

You will need to:

* Use `startapp` to create a folder
for the application and have Django create empty files like `views.py` and `models.py` in the `hello` folder.


* Create a `hello/urls.py` to route all requests to the hello application to a view function that you will write in
`views.py` - You can look at your `polls/urls.py` to see how the file is constructed in general and adapt it
to create `hello/urls.py`.   You will only need one urlpattern in the `hello` application.
You will only write a single view function that will *both* set a cookie and implement the session.
If your view function was named `myview`, the path will look as follows:


        path('', views.myview),

* Change the project-wide `mysite/urls.py` to mount the new application's urls at `/hello`.  Look at the line for
the `polls` urls and adapt it for yur `hello` application.

* Edit the file `~/django_projects/mysite/mysite/settings.py` and add the `home` application following
the pattern that you used to add the `polls` application to `INSTALLED_APPS` - again - the exact code
is something you figure out from looking at `dj4e-samples` or from the lectures.

Add a link to `~/django_projects/mysite/home/templates/home/main.html` with the following HTML:

    <li><p><a href="/hello">Test the session</a></p>

These instructions are telling you *what* to do now *how* to do it. This is
another DIY part of this assignment -
look at sample code and understand it - no more cutting and pasting instructions.

This assignment is not a lot of code. It is more about learning to read, reuse, and adapt code.
There is lots of sample code in `dj4e-samples` - probably
too much code.  If you just copy and paste everything from `dj4e-samples` it will be difficult to
make this work.  Sometime when looking at code written by others, it is important to know what
is going on to what *not* to copy.

Also make sure to check the auto grader for any additional requirements for this assignment.
