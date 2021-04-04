The Book of God, and Real Numbers
=================================

`Paul Erdos`_,
would refer to particularly elegant proofs
as coming from
"The Book",
short for
"The Book of God",
where God has written the most elegant proof for each theorem.
`Leopold Kronecker`_,
around 50 years earlier,
said
(loosely translated from the German)
"God made the integers, all else is the work of human kind."

.. _Paul Erdos: https://en.wikipedia.org/wiki/Paul_Erd%C5%91s
.. _Leopold Kronecker: https://en.wikipedia.org/wiki/Leopold_Kronecker

In this debate,
Kronecker has truth on his side.
Commonly, proving the theorem "a complete ordered field exists"
is referred to as "constructing the real numbers."
The Book does not have a proof for this theorem.
There are many proofs,
all of them flawed in different ways.

Different constructions of the real numbers expose
*trade-offs*:
some desirable properties follow some proofs,
while the proofs lack other desirable properties.
Which option is appropriate when
is a topic of hot debate.

"The Book" is a particularly dangerous metaphor here
because some proofs which look "elegant"
are bad for almost all circumstances!
Those who avoid trade-offs
end up picking the worst of all worlds.

Eudoxus Reals
-------------

Computers might not be people,
but someone needs to teach them math as well.
Specifically,
for automatically-checked proofs,
it is useful if the computer already
knows how to prove all of existing math.

The IsarMathLib_
project does exactly that.
It builds up math in the language
:code:`Isar`
that the "Isabelle"
system uses.

.. _IsarMathLib: https://isarmathlib.org/index.html

But computers are really not people.
This weird form of alien intelligence finds it natural
to define rings and groups
before the real numbers.
Because of that,
the
so-called
`Eudoxus Reals`_
make perfect sense.

.. _Eudoxus Reals: https://arxiv.org/abs/math/0405454

Eudoxus Reals are "almost homomorphisms"
from the integers to themselves:
functions where
:code:`f(x+y)-(f(x)+f(y))`
takes on only finitely many values.
It is a natural way to define the real numbers --
if defining homomorphisms first
seems like a reasonable thing.

For computers,
it is.
It also allows skipping past having to build
the rational numbers,
a nice side-benefit.
However,
those teaching human students are better of looking
for a better proof.

Dedekind cuts
-------------

Who doesn't love Dedekind cuts?
Those who have had to deal with the 16 different
cases proving multiplication distributes
over addition,
for one.

Professors get to shunt it off to TAs,
TAs get to shunt it off to exercises,
and students end up proving 4 of the special cases.
This is mind-numbing,
boring,
and thankless work.

It is a great way to torture
18th century students,
but everything is a great way
to torture
18th century students.
In this enlightened day and age,
torturing students seems less like a great idea.

Formal decimal numbers
----------------------

It is possible to
*define*
the real numbers as decimal numbers.
This requires completely unintuitive definitions
for multiplication,
as well as an annoying equivalence relation
(:code:`0.999....` is `1`).

Also, some of the case-based proofs
from the Dedekind cuts rear their ugly heads here
due to the ad-hoc handling of negative numbers.

Non-standard Analysis
---------------------

It is possible to construct non-standard rational numbers,
define the ring of finite non-standard rational numbers,
the maximal ideal of infinitesimals,
and divide to get the field of real numbers.

All the teacher needs to do is define a ring, maximal ideal,
prove the utlrafilter property from the axiom of choice
via Zorn's Lemma,
and explain how the field's axioms are all first-order properties
and so automatically apply to the ultraproduct.

If math curriculums included axiomatic set theory and logic in 1st year,
and did not need to deal with numbers until the 2nd,
this would be a great option.
In the universe where people studying math expect some exposure to numbers
before dealing with abstract set-theoretical topics,
this works less well.

Cauchy Sequences
----------------

Cauchy Sequences are the more intuitive cousins of the
non-standard analysis method.
They work great!
All they require is comfort with epsilon/delta techniques.
Which are taught in calculus.
Which needs the real numbers.

There's a hole in the bucket,
dear Liza.
In order to learn Calculus,
you must first understand Calculus.
For those students less into the
Zen method of teaching,
this is not a great option.

So, Tell Me What to Do!
-----------------------

Much like in the 12 step program,
the first step is acknowledging there is a problem.
The second step is to acknowledge that without help from a higher power,
you cannot find a perfect solution.

You muddle through.
You choose the least bad option,
and compensate for its flaws.