Leap Seconds
============

Time is political
-----------------

I am a time-measurement geek.
Time measurement is a fascinating topic,
and I can talk about it for hours.
One of the most fascinating aspects is just how
*political*
it gets.

Measurement is always political.
The French revolution lopped off heads
and invented the metric system.
But time measurement is even more political than most.
Indeed,
time zones are so complicated politically
that the official designation is
``Continent/City``
(for example,
``Asia/Taipei``)
so that when naming the time zone,
nobody has to argue about whether
Taiwan exists.

Much like this example shows,
the politics around time are not
always,
or even often,
along the right/left spectrum.
Nonetheless, where humans meet and have to make joint decisions,
politics exists.

What is a leap second?
----------------------

Take a specific point on earth that is relatively stable.
For example,
Disney World's
`Mission: Space <https://en.wikipedia.org/wiki/Mission:_Space>`_
attraction.
If you drew an imaginary line from the center of the earth
to the center of the Mission: Space attraction,
which way would it face at midnight?
Let's say you put a telescope,
align it with this line,
and take a picture every midnight.

Earth moves,
the galaxy moves,
and the pictures will be slightly different every night.
However,
you assume it faces the same
"way",
and that those pictures tell you a story about the relative movement
of the earth and the stars.

However, the earth spinning around its axis can take slightly longer
or shorter than 24 hours.
The rotation of the earth is influenced by the moon, geologic events,
and other hard-to-predict phenomena.
Because of this, if the imaginary line we drew is off by more than
1/86,400,
a second will be added to compensate.
This is not done by an
algorithm,
this is done by a committee of scientists.
Nothing can predict that:
you can only know about the next leap seconds a few months
ahead of time and prepare your system in an ad-hoc way.


Why a leap second?
------------------

Astronomers and astrophysicsts need to carefully measure things in the sky.
Being off by 1/86,400 would mean some of our important research would
be impossible to do,
because the data would be too noisy.
Similarly, space missions need to be able to accurately
identify locations in space.

In total, from 1972 to 2021,
a total of 27 leap seconds were announced.
At the beginning of this process,
an extra 10 "leap seconds"
were introduced for initial alignment.
Counting liberaly,
in the last 50 years,
less than 40 leap seconds have been introduced.

What's the big deal?
--------------------

Astrophysicsts and astronomers are not the only ones who care about time.
For some applications,
having an unpredictable day with an extra second could wreak havoc
with results.
Even if the results are not important,
needing to align many measurement devices with an ad-hoc heads-up
causes extra churn for anyone who needs time synchronization.

Since nobody wants to mess around with sattelites in orbit,
GPS time is not modified by leap seconds.
GPS time is currently ahead of
UTC (the time standard that takes leap seconds into account)
by 18 seconds.
TAI and Loran-C,
two other international efforts to measure time,
are also not modified by leap seconds,
and are currently 37 and 27 seconds ahead of UTC.

Even though GPS, TAI, and Loran-C times are different,
the difference between them can be specified by an algorithm.
The algorithm is comically simple: just add or subtract a constant
(10, 19, or 9, depending on which one to which one).
In contrast,
converting UTC to those times cannot be done with an algorithm.
For past times, an algorithm exists
(but is complicated)
and for future times, it is unknown.

What about my phone?
--------------------

If you are a modern person,
you probably own a smartphone with a GPS receiver.
The GPS receiver gets the position, but also the current time,
from the satelites.
Modern phones also use the network to synchronize time:
NITZ for 3G, and NTP for modern smartphones.
For example, Android_ uses
``2.android.pool.ntp.org``
by default
(although manufacturers will sometimes modify the server.)

.. _Android: https://android.googlesource.com/platform/frameworks/base/+/40caf8f4432acd2b9d9230b2b1371660521415c2/core/res/res/values/config.xml#820

NTP time, and NITZ time, uses UTC.
This means that smartphones all have *two*
notions of time: GPS time and UTC time.
Because of astrophysicists and astronomers,
less than 0.01% of the human race,
all users smartphones
(roughly 50% of the human race)
have to have two different timekeeping devices in their pockets.

More issues
-----------

As
`wikipedia notes`_,
randomly adding seconds to days causes problems for a lot of things.
The
"common workaround"
is to use TAI internally,
which would be great if not for the fact that the most common
time-sync protocol is defined by UTC.

.. _wikipedia notes: https://en.wikipedia.org/wiki/Leap_second#Issues_created_by_insertion_(or_removal)_of_leap_seconds

Are leap seconds evil?
----------------------

Leap seconds represent a cost to more-or-less all people
for the benefit of 0.01%.
Astronomy and astrophysics benefit all people,
but this sort of "trickle-down economics"
is normally frowned upon.
We usually ask people to bear the costs of their own needs,
and offer to support them with resources,
not global sacrifices,
if we think their cause is just.
Taxing all people for the benefit of the 0.01% is evil
by any reasonable ethical system.

There are no two sides.
Leap seconds are evil.
