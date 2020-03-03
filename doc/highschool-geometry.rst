High School Geometry Is Child Abuse
===================================

The
"modern"
textbook teaching geometry is
basically a badly translated
"Euclid's Elements",
together with,
hopefully,
some modernized exercises.
They all contain the same material,
because they are all based on the same
~2300 years old text.

In itself,
this is not bad.
Euclid was a pretty smart person.
Math does not change.
However,
while math is perfect and immutable,
humans are neither.
Euclid definitely was not.
He missed an axiom.

In 1882,
Moritz Pasch
discovered a missing axiom_.
Informally,
it states:
"If a line,
not passing through any vertex of a triangle,
meets one side of the triangle
then it meets another side."

.. _axiom: https://en.wikipedia.org/wiki/Pasch%27s_axiom

We can amend our geometry textbooks,
of course.
We should have done so for the last 140 years!
But it is worthwhile to consider not only why
Euclid,
professional smart guy,
as well as many smart students and teachers for,
literally,
over two thousand years,
could have missed it.

The reason is that what we call
"proofs"
in geometry,
following Euclid's definition from ~300 B.C.,
are nothing like what a mathematician would call proofs.
They are an intuition aid to proofs:
pictures made to inspire a proof.
But instead of teaching people to use that intuition
and write a formal proof,
we say that these pictures are proofs by themselves!

Of course,
intuition aids are invaluable teaching tools.
But confusing the teaching tools for the goal,
this is an injustice to every kid.

We could,
again,
amend our geometry textbooks:
not only to add the missing axiom,
but to show how to write a formal proof in geometry,
one that takes the axioms,
and manipulates them to arrive at the conclusion.
We could teach how to get inspired by the picture
to come up with a proof.

Now is the time to mention DeCartes' project,
to reduce geometry to algebra.
It succeeded,
though it would take another century to properly define what he did:
he showed that planar geometry,
as a formal theory,
taking Euclid's axioms and adding the missing one,
is equivalent to the theory of real-closed fields.

More years passed,
mathematicians made more advances,
and discovered that the theory of real-closed fields
is algorithmically quantifier-free.

In other words,
we can write an algorithm that will reduce every statement
about real-closed fields
into a quantifier free formula.
There are not that many quantifier free formula:
without free variables,
the only two,
up to equivalence,
are ``1=0`` and ``0==0``.
With free variables,
they define the solutions to a polynomial equation,
or a polynomial inequality.

In short,
we can write an algorithm that will solve any problem in a
"modern"
geometry textbook.
Our
"high school math"
curriculum is basically teaching kids to do the job
of a calculator,
poorly.

If we want to teach students how math works,
there is a much nicer way.
Finite set theory.
Here is how we would teach finite set theory:

First lesson:

* Present "naive set theory"
* Show Russel's paradox
* No homework

Second lesson:

* Explain how axiomatic set theory works: Von Neuman version
* Present some of the axioms (pair, union, replacement)
* Show how to prove the union of two sets is a set
* Independent work: prove the intersection of two sets is a set

Third lesson:

* Present some more axioms
* Show some more things are sets
* Show Venn diagrams as intuition aids
* De Morgan's first law: Show with Venn, then show formal proof.
* Independent work: De Morgan's second law

We would progress throughout the year,
presenting the formal axiom of Von Neuman Choice set theory,
and proving various results.
Finally,
we would get to the axiom of infinity.
There would be one lesson where we show the axiom of infinity,
but then we show that we can assume its negation.
This is finite set theory!

Now that we have all this theory,
we can build natural numbers.
Define the ordinals.
Define addition, multiplication.
Show that the rules apply.

We can even try to build the integers:
not the elegant construction with equivalence classes,
since we do not have infinite sets,
but we can just add
"formal negatives"
and define the rules of arithmetic the right way.

Having built the integers,
we can build the rational numbers:
again,
no equivalence classes,
but we can define them as irreducible fractions.

We would still use pictures as teaching aides and guides to develop
understanding.
No teacher would deny kids this tool.
But there would be a distinction between the tool
("use it to figure out an approach and learn what is going on")
and the goal
("write a formal proof").

This would fulfill the original stated goal of the geometry curriculum
without:

* Lying to kids without math
* Teaching them to be bad calculators
* Confusing them about what is a proof

Wouldn't that be nice?
