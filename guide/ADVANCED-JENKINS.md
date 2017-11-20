Advanced/Alternative Jenkins Configuration Scenarios
====================================================

In the main cookbook story presented in this guide, we allowed Continuum to
completely orchestrate our Value Stream, which means that it triggered our
Jenkins build job after a commit occurs.  There are at least two scenarios
where this might not work for you:

1. Jenkins server is located on a private LAN that the Continuum server is not
   able to communicate with.

2. You cannot or do not want to run a Jenkins build for every commit. One of our
   applications has a complicated CI process that runs thousands of integration
   tests that requires spinning up a dozen Jenkins workers and runs of well over
   an hour. On account of this, we cannot run this process on every commit as we
   have people committing constantly throughout the day. So we use Jenkins SCM
   polling so that Jenkins only runs at most every 2 hours.
   
Fortunately, both of these scenarios can be solved using the same technique with
only a slight variation. I will describe the process here.

Project Configuration
---------------------
If you recall, when we configured our project earlier, we added **Directives**
which controlled what Continuum does upon receiving a source code submission.
There was a directive called Package Into Phase that we used to create a package
and initialize it in the the Building phase.  This in turn kicks off a pipeline
which triggers a build of that commit.

In these scenarios, we cannot do that.  Instead, we will use a different
directive named **Assign to Pipeline**.  What this directive will do is tell
Continuum to create a "bucket" where it stores the submissions that are coming
in and associate them all with a pipeline job that is specified in the
directive.

I will walk through the configuration of this pipeline shortly, but it works
similar to the one we created for building our application before, except we
will not use the Jenkins Build directive in the pipeline, and will instead use
some directives to create the package and put it into the first phase.

In our Jenkins job configuration, we will use a Continuum plugin to call API
in Continuum to run the pipeline when the Jenkins build job runs.  In other
words, the Jenkins build job will run based on its SCM polling, and when the
job starts to run, it will then tell Continuum to run the pipeline.  This will
cause Continuum to take all of the commits it has stored in the bucket and link
them all to that instance of the pipeline run.  So essentially we are just
reversing the flow in which things work.

Let's explore this in more detail.

Project Configuration
---------------------
As noted in the Overview, we will add a different directive to our Project
configuration called Assign to Pipeline.  That looks like this:

![Assign Pipeline](images/assign-directive.png "Assign to Pipeline")

We use the same When condition we used before to limit this directive to commits
going to master or a release branch.  We then just need to specify the pipeline
we want to assign this to (which we have not created yet) and the group and
project. The group should be the branch name, and when the previously mentioned
bug is fixed you could specify a value of `[$ branch $]` here for that, but
until then we are going to extract the branch name from the ref.

    [$ ref.replace('refs/heads/', '') $]

Finally, you also need to specify the Project name. These three values combine
to form your bucket, which the submissions will be stored together in until the
pipeline runs.

Pipeline Configuration
----------------------



Jenkins Job Configuration
-------------------------

Links
-----

* Return to: [Overview](../README.md "Overview")


