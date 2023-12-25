I don't like monorepos
======================

I don't like monorepos.
I want to start with that so that it's clear.
I do have a bias.
What I
*don't*
have is a prejudice.
I stopped liking monorepos after quite a bit of experience.
Prejudice is bad because you make a judgement before having the fact.
After you have the facts,
it is perfectly fine to judge.
I've judged monorepos and found them wanting.

Microrepos problems
-------------------

Before diving into how monorepos work it is important to
understand the problems they are there to fix.
There are three problems that are usually touted as monorepos fixing:

* Standardization:
  it is easier to achieve consistent standards if everything is in the
  same place.
* Depdendency management:
  When updating a dependency, the person updating it
  can update all places that use the dependency in the same patch set.
* Cross-team collaboration:
  someone who needs something from an area of the
  codebase usually maintained by another team can do the work themselves.

These issues are real and,
sometimes,
painful.
If the team sets up a paid organization on GitHub,
for example,
then each repository will,
indeed, look different.
There will be
different permissions,
different workflows,
and different organization.


Monorepo tooling
----------------

Monorepos require all kinds of custom tooling.
Your enterprise or SaaS
GitHub or GitLab are not optimized for that.
Your CI system is not optimized for that.
Your local
tooling is not optimized for that.
Backup tools for source control are meh at best,
but I'm sure that whatever you get...is not optimized for that.
Nothing is.

All of these problems are fixable!
You can self-host a plain Mercurial,
use ReviewBoard for code reviews,
use Jenkins for CI with custom configuration,
and get one of the
popular monorepo-optimized build tools (like Pants) working.

You need to teach each person that joins the team how to use the tools.
You need to teach each person on the tools team how to maintain the tools.
This knowledge is the kind of knowledge that is the least career-useful.
The people who need to spend time learning all of it
gain little benefit in the job market knowing all of this.


Monorepo workflows
------------------

Monorepos can have
``OWNERS``
files that indicate who is the right person,
or team
to indicate who is responsible for what.
Without any more tooling,
there is still potential for confusion.

The file might be missing.
There might be conflicts.
The format of the file might be problematic.
In order to make sure that these do not happen,
*further*
tooling needs to be written.
There also needs to be training on how to understand
the error messages from the tooling
and how to address them.

Cross-collaboration
~~~~~~~~~~~~~~~~~~~

One workflow where
``OWNERS``
files might be important is the
"cross collaboration"
workflow.
In this workflow,
someone from one team submits a code change for
another team.

Presumably,
the standardization of the monorepo helped
in that running the unit tests,
both locally and in CI,
easy.
What about actually running the code locally?
It is possible that this is
*also*
standardized.
If so,
this is not because of the monorepo:
monorepos can,
for example,
build different kinds of artifacts that
are run in different way
and assume different environments.

If nobody from the owning team reviews the code,
this might mean some folk knowledge about the code
(or knowledge which is not directly in the repo)
might lead to the code having serious issues.
The team might only find out about these issues
when the problem comes up.
Unless the team is vigilant
this might be long after the change lands.

If the team does review the code,
this sometimes means the first point where they
see it is when it is "done".
At this point,
if the code needs some major overhaul or
the feature is not done correctly,
the solution is either to reject it and suggest
doing it from scratch
or
suggest minor improvements and land it with misgivings.

In order to avoid the dilemma,
the usual suggestion is to talk to the owning team beforehand.
At that point,
it might make more sense for the owning team to implement the feature.
Even if not,
some of the benefit of having a monorepo are lost
since the overhead of coordination often dwarfs the overhead of
cloning a different repository.

Sweeping changes
~~~~~~~~~~~~~~~~

There are two cases where
sweeping changes across the code are needed.
One is when a new best practice is adopted
and we want to update all code.
A more common one is when a dependency is changed
in a way which is backwards incompatible
and all dependent code needs to be changed.

Regardless,
allowing sweeping changes requires further tooling and training
in order to make them safe.
It is usually unrealistic to have people from each team review the
changes.
It is also unrealistic to assume manually running all products
which are impacted by code.
This means that the unit tests have to be
"perfect".

After the sweeping change lands,
it is impossible to revert.
Different teams will already have built on top of it.


Microrepos tooling
------------------

One way to fix the problems with microrepos is to adopt monorepos.
As shown above,
this requires writing quite a bit of custom tooling and investing in training.
The alternative is to
write custom tooling
and
invest in training
*without*
switching to a monorepo.

The question is not whether monorepo solve the problems.
The question is whether it is easier to write tooling to use monorepos
or tooling to use microrepos.
One answer is already clear:
for a
``$0``
price of custom tooling,
microrepos win hands down.
All the problems with microrepos remain,
but those problems are much better to have
than problems with monorepos without custom tooling.

This is one of the reasons why microrepos are often associated with
less mature engineering teams.
The engineering teams which are not mature will not be able to use monorepos
*at all*.
Like a peacock's feathers,
monorepos serve well as a
*signal*
of maturity
even without conferring any efficiency advantages.

Dependency management
~~~~~~~~~~~~~~~~~~~~~

In a microrepo world,
many dependencies will come from open source projects.
These need to be managed.
Tools need to be built,
or adopted,
to create artifacts from
*pinned*
dependencies
and to test
*updated*
dependencies.

These same tools can work for internal dependencies.
In a regular build,
these are pinned.
On a cadence,
updates are tested.


Standardization
~~~~~~~~~~~~~~~

The simplest tool for standardization is a bot that creates repositories.
Disallow permissions to create new repositories from all humans,
and have a bot create standard repositories.
Alternatively,
the bot can
"fix"
repositories which are created.

This requires a bot using the SCM APIs,
and possibly some git commands.
Not only is it easier than implementing custom Jenkins plugins,
but it also fails cleaner.
If the standard does not work for a particular use case,
an exception can be made and a repository that is not
"standard"
used until the tooling can support that.

Cross collaboration
~~~~~~~~~~~~~~~~~~~

Now with a more coherent ownership model,
it is easier to communicate with the owning teams in advance.
Assuming there is a basic agreement that the feature and strategy are sound,
*and*
that the team cannot prioritize doing it themselves,
someone external can work on the code.

The friction introduced is a good reminder that this is a last resort,
not the best option.

Sweeping changes
~~~~~~~~~~~~~~~~

At the point a sweeping change needs to be made,
it usually has to be automated.
If it is already automated,
it can be integrated with a bot that sends the
suggested patches to each microrepo.
This can include,
in the case of a backwards incompatible dependency change,
updating the relevant dependency to the new version.

Alternatively,
the dependency can document what changes need to be made.
When a team tries to update,
and the testing fails,
they can check the documentation to see what changes
need to be made.

Conclusion
----------

Monorepos do not solve,
by themselves,
any of the problems with microrepos.
What they do is make sure that no work can be accomplished
until the local tooling is of a certain quality.
This kind of heavy-handed way to ensure
that the quality of the tooling degrading
is an existential threat is closer to the tooling team
holding the engineering organization hostage
rather than supporting them.

Tools for microrepos,
when they break,
have better failure modes.
This is a feature,
not a bug,
to everyone except the tooling team.
Teams that support developers need to remember that their goal is just that.
Their goal is not to discipline,
control,
or force developers into doing
"the right thing".
