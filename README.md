Guide to Using Continuum and TeamForge
======================================

Overview
--------

This is primarily a HOWTO guide/cookbook for setting up Continuum, though in
relevant areas the instructions provided are specific to use with TeamForge for
version control and work items.  While this guide will attempt to explain
the concepts within Continuum there is an assumption of some basic
knowledge of the product and its terms.

Requirements
------------

These are the assumptions required for this guide:

* Continuum 17.3 or later
* TeamForge 17.11 or later
  * Project with a Git repository
  * Tracker with artifacts that are referenced in Git commits
* Jenkins server
  * Job configured to build the Git repository

Contents
--------

There are a lot of concepts to know and learn within Continuum.  The order in
which you want to learn different concepts is up to you. The order below is the
sequence in which this particular cookbook or "story" flows and is arranged such
that you configure an item before you need to reference that item in some other
part of the system.

In some places, this does mean learning about a concept perhaps a little sooner
than you might be ready for. However, if you follow this sequence you can set
up a working value stream and then revisit the concepts as you learn more.

* [Plugins](guide/PLUGINS.md "Plugins")
* [Pipelines](guide/PIPELINES.md "Pipelines")
* [Progressions](guide/PROGRESSIONS.md "Progressions")
* [Packages](guide/PACKAGES.md "Packages")
* [Projects](guide/PROJECTS.md "Projects")
* [Configure Package](guide/PROJECT-PACKAGE.md "Configure Package")

Additional Topics
-----------------

* [Jenkins Configuration](guide/JENKINS.md "Jenkins")
* [Testing it out](guide/TESTING.md "Testing")



More Information
----------------

[Continuum Community Guide](https://community.versionone.com/VersionOne_Continuum "VersionOne Continuum")


