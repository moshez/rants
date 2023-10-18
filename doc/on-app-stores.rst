On App Stores
=============

Rants are not supposed to be nuanced.
This rant,
despite all odds,
will be.

I have complicated feelings on
app stores.
They are the best and worst thing
to have happened to modern technology.
Separating the best from the worst is the most important thing
we can do.

What is an app store?
---------------------

The first thing to be nuanced about is
"what is an app store".
My definition will end up including things like
OCI Container registries
so there is definitely some room for debate.

An app store is a combination of a managed
SaaS service
and a local client
which allows an end user to
run applications on their device.
Sadly,
the least important part of the experience,
paying for the app,
took over the name.
Paying is not
*unimportant*
but it is remarkably less important.
App stores which are completely free
exist.

There are some things which are commonly,
but not always,
included in an app store.
Some of these are
"best practices"
for an app store.

* Some validation that applications
  comply with content guidelines
  (for example
  "appropriate for children or
  explicitly marked as not suitable
  for chidlren").
* User-based ranking/commening
  on applications.
* Predictive ranking of applications.
* Integration with a payments API
  for app purchase,
  in-app purchases,
  and/or
  app subscriptions.
* Some validation that applications
  uploaded are not malicious.
* Automatic updates to applications
  already installed.
* Managed sandboxing:
  an application declares which
  permissions it needs,
  a local sandbox limits it to these
  permissions,
  and the permissions are available
  for inspection in the UI before
  installation.

For my purposes,
sandboxes that support the last three points
(malware protection, auto updates,
and sandboxed)
are considered
to be using best practices.
Notice that all of those cover some range
on quality of implementation.
For example,
a sandbox which has weekly exploits announced
for breaking out of it
is barely any help.
The assumption is that these features are implemented with
"reasonable quality".

Why are app stores the worst?
-----------------------------

Before singing the praises of app stores
I want to be explicit about the downsides
of the model.
For the sake of this criticism
I especially consider
"app-store-only"
ecosystems.
In such ecosystems
installing software
*outside*
an app store is
either impossible
or unreasonably difficult for the
modal user.

In such ecosystems
an app store is a
*natural*
monopsony
*and*
a monopoly.
Application writers
("ISVs"
or
"Independent software vendors")
have to use the app store to
sell to their customers
and
end users have to use the app store
to install software.
The usual issues with market failures
in the presence of a
monopsony
and
a monopoly
are combined.
This is further excerbated by
the app store
achieving that status
by being integrated with the
device vendor.
This means that competing app stores
are explicitly disallowed!
Even in cases where competing app stores
are not explicitly disallowed,
app stores are
usually a
winner-take-all
for a given stack.

Why are app stores the best?
----------------------------

Flash-based websites
and games rose to prominence
in the late 90s
and early 2000s.
This was inspite of the fact
that the runtime itself was
of poor quality
and developer tooling was not
much better!

The only reason they rose to prominence
was that they had some of the features
that app stores had.
The flash plugin provided a natural sandbox.
The fact that it run inside of a browser
meant installation was simple and fool-proof.
Keeping the application up to date required
no more than reloading the web site,
which could be done manually or triggered
by the app itself.

In an era where installation meant downloading an
``exe``
file from somewhere,
double-clicking it,
and hoping for the best,
this was a big step up.

One reason
Flash
has lost its prominent place as a runtime
is because app stores are,
in almost every possible way,
a superior.
(The other reason,
beyond the scope of this article,
is the rise in the
technology stack available
for Javascript-based
front-end programming,
but this is only tangetially related.)

App stores,
it turns out,
was what the modal end user wanted
all along.
A managed experience for software
installation
and
uninstallation
which automatically sandboxed
applications
and updated them when it was ready.
The
Apple App store,
in particular,
almost single-handedly revived
the software niche of the
"small ISV".

The hope for a better life
--------------------------

You take the good,
you take the bad,
you take them both,
and then you have
the facts of life.
App stores,
for worse or better,
are here to stay
as a fact of life.
It is likely that they will increase in prominence.

Many people still install software
"the old way"
on
their personal computer
but have bought in to using an app store
on their phone or tablet.
Both Windows and Mac
have a
PC-based
app store
as well.
Some features,
such as enhanced sandboxing,
are only available for applications
installed using the app store.

The future is for PCs,
as well as phones and tablets,
to disallow,
or at least make it difficult,
to install software without using
an app store.
This has many benefits:
an app store is a great central place
to control against malware.

Regulation
----------

Government regulation,
as a general rule,
can cause market distortion
and actual harm both
to industry and consumers.
Usually,
it is best avoided.

All but the most staunch
free-market advocates
agree that government regulations
for monopolies and monopsonies
is sometimes the best option possible.
The usual market forces
("the invisible hand")
act more slowly,
and often not at all,
in those cases.

At this point,
the question should not be
"should we regulate app stores".
It should be
"how do we regulate app stores".
As mentioned,
app stores are natural
monopolies
and monopsonies.
Moreover,
they are often
*explicitly enforced*
monopolies/monopsonies:
the device vendor makes it hard
to install
competing app stores.

The
*simplest*
regulation is to disallow
this practice.
Require device manufacturers
to allow for some process
where an app store is added to the device.
This process does not need to be as easy
as installing an app
but it needs to be easy enough.

For example,
the following things would
probably make sense:

* Require extra verification of user intent and control
  (MFA, separate UI).
* Require further validation of app stores and originating entity
  (for example,
  registering a DUNS number).
* Allow limiting the app stores on managed devices
  (either as corporate managed devices or in parental controls).

The most important thing
would be to explicitly disallow,
using incentives or disincentives,
controlling which app stores
are available when the device is first received
by the end user.
This allows vendors to offer multiple app stores,
our of the box,
or even customize an initial experience
of
"choose from the following app stores".

Because of the outsized opportunity for the device manufacturing,
the basic sandboxing capabilities offered by the OS
should be available under a
"non-discrimination"
clause.
The device vendor app store is not allowed to
use any sandboxing facilties that are not publicly
documented for all app stores to use.

A slightly more extreme regulation would be to disallow
cross-ownership
of a device vendor and an app store,
while still enforcing
non-discrimination.
This will further serve to discourage favorable treatment
of one app store over another.

Since app stores are,
even with the guidelines above,
likely to remain a natural monopoly/monopsony,
there is room for further regulation.
An app store that is deemed as a monopoly
can be further regulated to limit its ability
for pricing and content interference.

An example guideline is that
when sorting the applications by
"times that an application would have been updated,
if there was an update,
per week"
(as a proxy for app store popularity),
the top app store is not allowed to take a bigger
cut
off of any integrated payment rail,
or have stricter content guidelines enforcement,
than the next app store.

This guideline would mean that the
*second biggest store*
would constrain the ability of the biggest store
to take more money,
or to unreasonably constrain content.
This still allows
"specialty stores"
with either extremely strict or extremely lax
content guideline,
or fairly complicated payment integration
contracts,
while making sure the general stores
compete on other features.

Summary
-------

App stores are a great technology.
They need to be better regulated.
