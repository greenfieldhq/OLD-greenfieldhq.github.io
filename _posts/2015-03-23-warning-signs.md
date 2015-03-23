---
layout: post
category :
tagline: ""
tags :
title: "5 Warning Signs that Your Development Team Needs Help"
description: Some top warning signs to look out for.
author: mike_munroe
---
{% include JB/setup %}

For some development teams, the following things might be taken for granted, but
if any of the following are issues within your team, you should investigate ways
to remedy the shortfall.

###1. The code your developers are writing is not contained within a source control system
Source control, also referred to as version control, is a system to track on
going changes to the source code for your application. Most modern teams are
utilizing
[Git](http://git-scm.com/book/en/v2/Getting-Started-About-Version-Control), but
another common source control system is [SVN](https://subversion.apache.org/).
Utilizing a source control system allows allows for your developers to see the
revision history for changes, and who made those changes. Depending on the
souce control system, there are also a lot of tools for managing development
efforts moving in parallel.
We utilize Git, hosted on GitHub(https://github.com/), for all of our client
work. GitHub has a powerful UI for reviewing pull requests, a set of changes a
developer wants to share with other team members for review before being
commited to source control.

###2. The database for your application is not backed up on a regular basis
We all know how important back ups can be, but we never realize how important
they are until one is needed. All of your important development assets should be
getting backed up regularly, but backing up the database for your application is
of the utmost importance. Not having a regular back up occurring is a sign of
organization missing with your team. There are a lot of tools that can be
utilized for completing back ups on a schedule, but often a cron job is enough
to run a back up task and place the back up file in a secure location.

###3. Areas within your application take seconds to load
In general, your users are expecting to see pages load in under 1 second. Even,
if the application is not delivered within a browser, plan for similar
expectations. Performance issues are always going to be a drag for your users.
Aside from the issues above, performance issues could be caused by a multitude
of different problems. It's possible that the UI that has been programmed is
causing excessive load time, it could be a slow query again your database, it
could be a fast query that is getting called an excessive amount of times over
and over again, or it could be some calculation being completed in business
logic code taking a long time. If you have some performance issues within your
application, but you don't have any solid evidence on where the problem lies,
it's time to pull back the covers and isolate where the problems lie.

###4. You have no automated tests
Testing can kick off some heavy fighting some times depending on who is involved
in the testing discussion. Some believe you need a certain quantifiable amount
of automated test coverage to be thought of as a well tested application. I
don't want to get caught in an argument over how much and what should be tested
because testing strategies can change from team to team depending on the
application being developed and its infrastructure, but I am arguing that if you
have no automated testing coverage, especially for core areas of your product,
it's time to investigate and set your testing strategy. If you have a team of QA
engineers manual testing things, that's great. Talk a few of them to bite off
doing some programming and getting you some automated coverage.

###5. There is no confidence in status of how you are trending against your next release
Your last 3 releases were behind schedule. You're currently working on your next
release, but you can't tell if you are on schedule or behind. Your basing the
status of the release on the feel of how things are going. If you really want
to understand something, you have to measure it. Teams have different strategies
for measuring progress. With our clients, we typically break up releases into
smaller two week sprints. Each sprint has features within them with a
quantifiable measure of estimated work, often referred to as story points. As
we work through sprints, an average velocity of work completed during a sprint
falls out and is useful in guaging the amount of work the team can complete
during a sprint. For a multitude of reasons, a project could come in late for a
planned release or maybe even short of the budgeted time period. If you are
measuring progress, you can quantify progress and plan accordingly, but going
blind by feel is a recipe for painful outcomes. 

Greenfield is a Ember.js and Rails consulting firm based in Boston, MA, but we
have a lot of experience with managing these type of problems. If you need help
investigating solutions for these issues within your team, please
[reach out](http://greenfieldhq.com/#/?anchor=contact).
