Packages
========

We were first introduced to Packages when we setup our pipeline for build.
Now we are going to start to connect the dots.  A package is the piece
of software we are delivering.  We could have a big application made up of many
parts, but if we deliver it all as one unit most likely we will only define one
package to represent the application.  This is especially likely if the
application is all stored in one source code repository.  Conversely, if you
have more of a service-based architecture where individual services are
delivered and maintained separately, then you definitely would want one package
per service.

On the *Admin* menu click on *Packages*.  Then click on *Add New*.  You will get a
pop-up dialog to provide a Name and Description.  Once you have added the
Package, click on the Progression tab.  This is where we will do most of the
work.  First, we select the Progression we are going to use for this package.
In the Progression drop-down, select the Progression we created in the previous
step.  This will load in the phases from our Progression.

You can just go ahead and check the *Promote Automatically* check box on each
Phase.  This means that once all activities for a phase have completed the
package will automatically be promoted to the next phase.  If you did not check
this box, you would have to have an action in a pipeline perform the promotion
based on some condition in the pipeline.  We are not going to need to do this
for our example.

The next steps would be to add activities to each phase.  This is where we will
indicate a pipeline to run, but before we do that, this is one place we are
going to need to stop and jump around.  We are going to have to create our
Project first and then come back and finish the Package configuration. We will
do all of that after we create our Project in the next topic.


Links
-----

* Next Topic: [Projects](PROJECTS.md "Projects")
* Related Topic: [Configure Package](PROJECT-PACKAGE.md "Configure Package")
* Previous Topic: [Progressions](PROGRESSIONS.md "Progressions")
* Return to: [Overview](../README.md "Overview")


