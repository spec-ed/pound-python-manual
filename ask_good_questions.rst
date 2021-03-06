Asking Good Questions in #python
================================

Before You Ask
--------------

Google
******

Search the internet for the solution to your problem.  You will often find a
workable example of what you are trying to do (if it is indeed possible).  Do
be careful, however with solutions you find.  `StackOverflow
<http://stackoverflow.com/>`_ is rife with bad advice; before using the number
one answer, read the comments and other answers.  Look at many solutions to the
problem and see what they have in common.

Documentation
*************

If you have not already, read the documentation of any modules you are using.
They may explicitly cover any problems you are having.  Along the same lines as
the documentation, check any public issue trackers, mailing lists, or forums
associated with the module or package in question for any user with the same
problems.

Read the Code
*************

You may be able to find the answer to your question by reading the code of the
module or package you are having a problem with.  This may also enlighten you
on the way the module author intended for you to use the module.

Asking Your Question
--------------------

Know What You are Trying
************************

The first response to many questions in #python is often "What are you trying
to do?".  The person answering your question is trying to understand the
problem.  All to many times a new user will ask a question about why their
implementation of something does not work, and when asking for help, focus only
on a small part of the implementation that is breaking.

In order to help solve your problems, those answering questions need to
understand the problem your code is trying to solve.  That is often more
important than the details of the code you have already written.

Identify Your Problem
*********************

You should have a full understanding of the problem you are having.  This
sounds kind of odd at first.  It is obvious that you are having a problem with
some aspect of your application, and you likely do not understand why; after
all, if you did, you probably would not be asking the question in the first
place.  What you have to understand is what your code is actually doing, and
where it is breaking.

This is the counterpoint to the previous section;  This is all about
implementation detail.

Think About your Question
*************************

It is a good practice to write your question out in a word processor or text
editor before asking it in channel.  This gives you the opportunity to check if
the question makes sense, and if you have provided enough information to a
potential helper to get you an answer.

Try it And See
**************

Before you ask a question if some operation is possible, try it yourself.
Write a small python module that demonstrates what you are trying, and run it.
If it runs, then you have your answer without asking.  If it does not run, or
does not run correctly, you have a basis from which to ask your question (this
should only be invoked if you are unable to share your code, see bellow).  Do
this step even if you intend on showing your entire codebase.

For advice on writing this module, see http://www.sscce.org/.

Show Your Code
**************

It saves a lot of time and energy to have a web-paste or a link to a hosted
version control site ready when you are asking a question.  This allows the
helpers to see the actual code that is causing an issue, and they may be able
to find an apparently unrelated piece of code that is the root cause of your
problem.  They can also make suggestions about the structure of your
application to help you find a better way of doing something.

If you cannot share your code for some reason, you should have, previously
prepared, a module with everything in it required to show the problem you are
having.  This is what you should provide in a web-paste if you cannot show your
actual code.  Keep in mind, that this is no substitute to showing your actual
code.

Do's and Don't's
****************

Do
  - Have your reasonably well worded question ready
  - Have a link to your code ready
  - Make a reasonable effort to write in grammatical, well-spelled, English
  - Be patient.  A good question often does not have a quick diagnosis or
    answer
  - Help others while waiting for an answer to your question.

Don't
  - Ask if anyone is around the answer questions
  - Ask if someone knows the module with which you are having trouble
  - Declare that you have discovered a bug.  You may have, but more often than
    not, you are not using the module as the author intended.
  - Demand an answer.  #python is a free service provided by volunteers in
    their free time.

Frequently Asked Questions
--------------------------

These are genuinely asked quite often.

'Why "NO PROJECT EULER"?'
*************************

At the time of writing this document, there had been an admonishment in the
channel topic forbidding discussions of `Project Euler
<https://projecteuler.net/>`_ problems.  The reasoning behind this rule is
quite simple; the goal of #python is to help people write better python code.
Project Euler's goals, while using python, are to help people understand
mathematic principals through programming.  More often than not, those who
asked questions relating to Project Euler were not having problems with Python
concepts, but with the mathematical concepts they were trying to solve.  As
these are not problems that exist in normal programming with Python, and that
the influx of users asking for math help was drowning out the users asking for
Python help, it was decided to ban questions relating to Project Euler.

"I asked about using <foo>, not <bar>."
***************************************

Warning: This section is opinionated.

That is a statement, more than a question, but it is a common complaint.  New
users, or users new to a problem space, will often ask questions about using an
old third party module or a module from the standard library, and be told by
the helpers to use a different library.  This often takes the form of a new
user asking about problems with the socket library, and being told to use
Twisted.

Python is advertised as a language "with batteries included" - meaning that it
has an extensive standard library of useful modules.  The problem is that
modules in the standard library are very old and cannot be updated to use
modern advancements.  Once a library enters the standard library, it cannot be
updated until the next release of Python itself (which, at the time of this
writing, has an 18 month minor-version release cycle).  At these
year-and-a-half release marks, only conservative changes to the API can be
made, and old APIs only removed with a previous release's deprication notice.
The API cannot change at all in a patch level release (with the exception of
fixing a bug in the api, but this is rare).

Further, some of the modules in the standard library are quite low level, and
intended to be used by seasoned programmers.  The socket module is one of these
modules.  Without a deep understanding of networking, you will make a mistake.
Even with a deep understanding, it is a hard module to use correctly.

Developers who are experts in these low level modules have created, and
maintained for a long time in many cases, third party modules and packages that
give other users a more sane interface to low level functions, and hide the
hard-to-implement-correctly details.  In the case of networking, Twisted is
highly recommended by the users of #python.  Other problem spaces are similar
(urllib vs. requests.  I could go on, but the list is extensive).

On the other hand, some third party modules are better than others.  In the
problem space of Object Relational Mappers, there are several options.
SQLAlchemy is, at the time of this writing, considered to be one of the best
options in that space.  Peewee on the other hand, is considered one of the
worst for many reasons.  It is highly likely that a user with a question about
Peewee will be directed to SQLAlchemy.  (Sorry, Peewee developers).

So why where you told to use something else?  Because there is a better, well
known, solution to your problem.  It should be mentioned, that you are free to
ignore their advice, and the wisdom of the community may not be 'right', but if
getting support from #python and from around the internet is something you
depend on, then using the libraries that are popular and recommended by the
community will greatly improve your chances of success.

"Why do you have to be so mean?"
********************************

First of all, on behalf of the Python community, I apologize.  If someone was
harassing you, calling you names, using racial epithets, or were being
discriminatory in any way towards you, please ask to speak to a channel
operator, or join #python-ops and tell them what happened.  Include, if you
have it, the time (and timezone you are in) of the problem, and they will do
the best they can to prevent that from ever happening again.  That behavior is
unacceptable, but thankfully very, very rare.

Something that exists in our community, that great effort has been put towards
changing, is an unnecessary level of bluntness, bordering on rudeness.  This
often comes in the form of terse, demeaning answers to questions.  This is not
something we, as a community, endorse.  If this has happened to you, please
tell the person, politely, that what they said was offensive or rude.

The people in #python come from all cultures and walks of life.  Some may have
different values than you, and may not consider what they said or did to be
rude.  As an international community, giving someone the benefit of the doubt,
that they did not intentionally offend you, may be prudent.

No excuses can be made for abusive users.  If a user is constantly rude, but is
not discriminatory, it may be prudent to ignore them.  All IRC clients are
capable of blocking messages from a user, I leave it as an exorcise to the
reader to discover that mechanism in your client.

"But its a .py, why wont you help me?"
**************************************

This comes up when a non-programmer user joins #python with a bug in code they
did not write.  This often takes the form of an application that a Linux
distribution ships or the user downloaded from the internet.  Whatever the
application is supposed to do, it has a bug, and the user asks in #python for
help.

Unfortunately, there are an unknowable number of applications written in
Python, some better than others.  It is impossible for a small group of helpers
to provide help for applications that are buggy, close source, sufficiently
ancient, or sufficiently complex.  The goal of #python is to help people write
better code.  We don't have the resources to fix everyones bugs for them.

Recommended Reading
-------------------

- http://www.catb.org/~esr/faqs/smart-questions.html
- http://sscce.org
