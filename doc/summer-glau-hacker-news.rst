Contra the "Handmade Manifesto"
===============================

The Handmade manifesto,
unfortunately,
is a bit vague.
Instead,
this rant will
"weakman"
by
replying to a
`HN comment`_
in the style of
`Summer Glau`_.

.. _HN comment: https://news.ycombinator.com/item?id=37602342
.. _Summer Glau: https://xkcd.com/406/


   Our computers are orders of magnitude faster than they were.
   What new features justify consuming 100x or more CPU, RAM, network
   and disk space?

Good question! Let's go through your detailed examples and see.
Instead of doing this in order,
I will start from the end.

CI/CD pipelines
---------------

For this,
assume the central thesis of the argument is correct.
Programmers should be using
low-level languages
with zero cost abstractions
in order that increases in hardware power
are immediately reflected in end-user
software performance.

Take this,
albeit questionable statement,
as a given.
The comment ends with the following:

    Slow CI/CD pipelines are a completely artificial problem.
    There's absolutely no technical reason that they need to run so slowly.

The other parts
*seem*
wrong to me.
I am not a product software engineer.
Not only do I not work on the
UI, frontend,
or whatever part that actually runs on
the computer people have on their desk
or their laptop,
I usually don't write the backend
that is running on a server either.
It is not my domain of expertise.
I
*could*
be wrong about it.

However,
I have spent a long time on
CI/CD
pipelines.
It has been my main job for a few years
and
a big part of my job for over twenty
years.
This is something I can speak about
from a position of earned authority.

*This is incorrect.*

The
*default*
of a
CI/CD
pipeline is to be slow.
In some environments,
through heroic efforts,
you can make the pipelines
faster.
With modern tooling
this is made much easier.
Even with the
*best*
for-pay
modern tooling
*combined*
with the latest
open source tooling,
any real situation where
CI/CD
pipelines are
"fast"
turns out to have involved
local work that is hard to generalize.

The author argues for
few abstractions.
This means that the languages
that are going to be used are
"low level".
In practice,
the most popular ones are
C, C++, and Rust.
I suspect the author is a big
C
proponent:
all others include
some abstractions that
cost some performance.

The CI/CD pipeline
now has to build a big
C
application.
Compiling a lot of C
files can be extremely slow.
C,
especially when trying to avoid
higher level abstractions like the
"glib"
library,
is a verbose language.
The compiler needs to read the code,
and optimize it,
for every file.

Using something like
``make``
with no further configuration will
compile it one file at a time.
The author says that
"CI/CD pipelines being slow is artificial",
not that
"CI/CD pipelines being slow is possible to fix".
It is possible to convince
``make``
to parallelize.
Tuning that parallelization in a given situation
is non-trivial.
It is easy to make that slower than not doing
the parallelization.

Assuming the software should be good,
as well as fast,
automated tests should be run.
The best time to run them is
*pre*
merge.
Otherwise,
test breakage on the main branch is rampant
and eventually,
the tests are ignored.
C having few abstractions
it is sometimes non-trivial to test enough
using fast unit tests.
Much of the value will come in by running
integration tests in the
CI/CD
pipelines.
Those tests can be slow.

Languages like
C++
and
Rust
come with their own challenges for compilations
which can make
CI/CD
slow.
Rust's compiler is remarkable for its slowness.
C++ has much of the code in header files.
Avoiding compiling the code in header files
multiple times is a subtle dance
in the CI/CD pipeline.

There are ways to fix it!
Distributed compilation,
caching compiled artifacts,
and more
are all techniques that can be used.
Configuring a good build cache,
configuring a good distributed compiler,
or
doing any of the other things that make
CI/CD
faster
is not a trivial thing.
Companies employ tens of people
just to maintain these kinds
of infrastructure,
let alone make significant improvements.

Software features
-----------------

Now that we know the author is less than credible,
it is time to look at the rest of the statements.
This is not an ad-hominem,
merely a counter to an argument from authority:
there is no reason to pre-emptively assume
the author without any further evidence.

Email
~~~~~

   Is my email software doing orders of magnitude more work to render an email compared to the 90s?

It renders HTML, allowing for formatting.
Most modern stuff will automatically hide what it heuristically detects as
"text being replied to".
It will also heuristically detect,
and sometimes hide,
signature.
You can configure it to auto-download images
or do it on demand.
If you do the latter,
it takes little time to download and re-render the e-mail.

It also renders some of the e-mail into clickable
"hot areas"
so that when you click on the
"From"
area,
you can see what other e-mail the person sent you.
It will also pre-emptively fetch
related archived e-mails
and display
"teasers"
from them,
so that you can click on them to reveal more
if you need further context when you're reading.

So,
um,
probably orders of magnitude more?

Chat
~~~~

    Does discord have that many more features compared to mIRC that it makes sense for it to
    take several seconds to open on my 8 core M1 laptop?
    For reference, mIRC was a 2mb binary and I swear it opened faster on my pentium 2 than discord takes to open
    on my 2023 laptop.

You, um, swear?
You have a graph to show the difference,
right,
with error bars and stuff?
No matter!

Discord shows saves history.
It connects to multiple logical
"servers",
which have channels divided into
high-level topics.
It gives you the ability to mute topics
for a certain amount of time.
Management of the admin side,
including roles and permissions,
is all UI based,
not depending on integrating with bots
and sending them commands that can sometimes work.

The search functionality works so well that some people
try to pretend it's a replacement for documentation.
It's not,
but the fact that the temptation is there is a testament
to the quality of the search.

There are emoji replies,
with custom emoji available.
The emoji are searchable by text
and it also remembers the recent emojis.
There are threads and replies.

There is way to ``@`` a specific role.
There are spoiler tags
and pre-formatted rendering.
It pre-fetches links and renders
a summary.
There is probably more that it does.

This is ignoring Discord's functionality to integrate
voice calls,
video chats,
*and*
screen sharing.
Those sound like complicated features.



Productivity
~~~~~~~~~~~~


    As the old line from the 1990s goes, "what Andy giveth, Bill taketh away."[1]
    (Andy Grove was CEO at the time of Intel.)

Considering most people used Microsoft software successfully,
it is possible that Bill didn't
"take away"
as much as
"made use of".

Proposed solution
~~~~~~~~~~~~~~~~~

The author
summarizes the issue:

    By the standards of 1995 we all walk around with supercomputers in our pockets.
    But you wouldn't know it, because the best hardware in the world still can't keep pace with badly written software.

Presumably,
the author suggests
to
keep
using
`mutt`
and
`mIRC`.
It is interesting that it is possible to use
both.
IMAP4 is still widely supported.
There are popular IRC networks.

Even people with older computers,
for the most part,
choose to use other solutions.
While in the abstract
it could be possible that the reason is that
Gmail
and
Discord
are marketed so well that people do not know about them,
this requires far more evidence.

Consider the effort in teaching
*programmers*
to use the Git command line.
Extraordinary claims require
extraordinary evidence.
The author provides no evidence
that people would love to run
Mutt
and
mIRC
on their laptops,
let alone their phones.

It has only gotten
*easier*
in recent years.
Most people run either
Windows laptop that support
WSL2
or
Mac laptops
that have direct access to
"brew".
Chromebooks can enable the
"Linux development environment".

Even with this widespread ability to use
mutt
for e-mail
and
mIRC
for chat
an overwhelming majority use
web-based mail clients
and
Discord.
Some evidence that they would switch
should be possible to gather.
In this case,
absence of evidence is at least arguably
evidence of absence.


People seem to value the features
in the modern systems.
It would be suprrising if they cared more that
when opening these on terminal windows
they take 0.1s instead of 0.2s to open.

It is at least a reasonable hypothesis that maybe
most people value the features that
the
Gmail UI offers that mutt didn't,
or that the
Discord UI offers that mIRC didn't,
more than an extra 0.1s when they open the application.
There is little value of walking around with a supercomputer in your pocket
if you take no advantage of its power to make yourself better off.


Programmer diligence
--------------------

The author,
having concluded that the features in the modern systems
are not the reason why people use them,
needs to find some reason why programmers nowadays
use modern programming languages and abstractions.

Continuing in the trend of refusing to gather evidence,
the author hits on two possible explanation by
"instinct".

    My instinct is that as more and more engineers work "up the stack"
    we're collectively forgetting how to write efficient code.
    Or just not bothering.

Not only is there no evidence provided for the instinct,
the author is not even sure what the real reason is.
They advance two
*competing*
hypothesises.
The first is
*ignorance*.
People are
"collectively forgetting".
By that I am assuming that the people who knew how to do it
are churning out of the industry and
that new people are not learning it.
Otherwise,
the word
"collectively"
would be redundant.
The other hypothesis advanced is
"apathy":
not bothering.

The commitment to avoid gathering evidence is so strong
that even when the author is not sure about something,
no effort is made to satisfy the curiousity.
Instead,
the author continues by guesswork to assume the last
hypothesis mentioned is the true one:

    Why optimize your react web app when everyone will have new phones in a few years with more RAM?

The assumption that the programmer
*does*
have the skills,
or could acquire them,
to optimize the react web app
but chooses not to.
It is not clear why,
in retrospect,
the comment was not edited to remove the
"collective forgetting"
hypothesis and focus on this one.

Now that we have a specific hypothesis to content with
it is easier to argue against it.

    If the users complain, blame them for having old hardware.

Blaming users is not the business-savvy move the author thinks it is.
Now that smartphones show only marginal improvements year-on-year,
and laptops improvements are even less noticable,
many people keep hardware around for longer.

This trend is even stronger in
`LMICs`_
(low/middle income countries).
With the market saturated in the
"high income"
countries
many companies try to expand into
LMICs.
Many people in these countries buy used phones
or have access to local expertise for replacing
batteries and screens
to keep older phones working longer.

.. _LMICs: https://www.oecd.org/dac/transition-finance-toolkit/LIC-to-LMIC.pdf

There is plenty of business opportunity into optimizing your
React Native
app
to use less memory and require less CPU.
LMICs
often have no entrenched players,
so the first company to establish presence
can often get a lot of users.
Even if individually,
these people have few resources,
they are sophisiticated consumers
and in aggregate
the business opportunity is remarkable.

User rights
-----------

    I find this process deeply disrespectful to our users.

I do have to wonder what this is based on.
There is a suggestion that a different set of engineering
trade-offs
would make users better off.
There is little to show that any user engagement has been done.
It is likely that different people prefer different things.

Aggregating trade-offs into specific recommendations is hard work.
This is the job of UX folks
who go out and interview users.
They can simulate a small delay and see how it impacts
impression
and
usability of a software product.
There is no evidence that this has been done.
At the risk of appearing presumptious,
I suspect that the usual answer of
"it depends"
is true.

There is no indication in this that the real problem is not having
good UX processes.
A general solution of
"make software faster and more memory efficient"
is advanced
as a cure-all.

    Our users pay thousands of dollars for good computer hardware because they want their computer to run fast and well.

It is important to note that even in this
relatively
evidence-free rant
the author concedes that
"and well"
is part of our criteria.
When trying to optimize for software quality,
reducing bugs and keeping software to spec,
it is not impossible that abstraction presents
a net gain.

At the very least,
higher iteration speeds allow more experimentation to see
what users value.
In addition,
memory-managed languages reduce memory allocation bugs and crashes.
Using powerful abstractions that have the benefits of more development time
and testing
can lead to less user-visible bugs.

Running software inside sandboxes,
like the browser,
results in slow-downs
but also allows for features like safe auto-updates.
So safe,
and so effortless,
that for most end-users
pressing the little
"reload"
button in their browser does not even register as
"upgrading software".

None of these trade-offs
of software quality
against
software performance
are discussed here.

Profit and loss
---------------

    But all of that capacity is instead chewed through by developers the world over trying to
    save a buck during development time.

Saving money for the company you work for is not a bad thing
in and of itself.
It should not be done unethically,
but there is no indication that this is the case
at hand.
Such cost savings can make the company more profitable,
earn the programmer more money,
or the cost savings can be passed on to the users.
In a reasonably efficient market,
gains will be split between all of them.

Most bigger software companies are publicly traded.
The biggest owners of publicly traded companies are
401K funds.
So this
"saving a buck during development time"
is divided between the programmer,
the consumer,
and retirement funds.
It seems like making this choice is both
ethical
*and*
more immediately rational.

If this is an argument
*against*
progammers
"saving a buck during development time"
because it
"chews through capacity",
it is a poor argument indeed.

    Every hardware upgrade our users make just becomes the new baseline for how lazy we can be.

I am not sure what the word
"lazy"
means in this context.
If using these high level abstractions allow programmers to maintain
reasonable
work-life balance
instead of being worked for 80 hours weeks to meet deadlines,
there is value in that too.

Programmer burn-out is a real problem.
It is a problem with both immediate effect on programmers,
who are humans whose well-being has inherent self-worth.
It is also a problem for the software industry
since programmer churn can end up increasing costs
and
reducing software quality.

In the aggregate
we are all better off if this is reduced.
If the cost of that reduction is that modern software
takes a second to open on people's computers,
this might be acceptable.

Conclusion
----------

The author is observably wrong on some things.
For the things that are harder to evaluate
there is no evidence provided other than
vague impressions and instincts.
The author also staunchly refuses to acknowledge
that engineering choices have trade-offs
and to evaluate these trade-offs.

Furthermore,
even on its merits the argument fails to advance
the original case.
The author seems to agree that producing software
using modern stacks and tools does make programmers
more efficient
and easier to train.
