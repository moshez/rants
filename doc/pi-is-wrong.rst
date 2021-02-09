Pi is Wrong
-----------

This is not an article about Tau_.
(Of course Tau is the correct way to think about circles
and not Pi.
This is obvious and will not be mentioned further.)

.. _Tau: https://www.math.utah.edu/~palais/pi.html

Pi is a famous constant.
People celebrate Pi day,
memorize Pi's digits,
and engage in other forms of math-inspired play around in it.
But does it deserve its fame?
What is Pi actually doing?

Instead of talking about that,
let's start with a tangential issue.
We expect differential equations that describe the real world
to be *position independent*.
This means that the free variable should not appear in the equation,
otherwise physics would look different based on where you are.

When thinking about such differential equations,
we can think about the
simplest one: `f' = f`.
A function whose deriviative is equal to itself.
One such function is too simple: `f(x) = 0`.
This constant function has a derivative of `0`,
which is equal to it.

Can there be other solutions?
It's not obvious but let's a function that is
*not*
always `0` and solves this equation,
if it exists, `p`.
Now, `p` can *never* be `0`, because this equation is position-independent.
If it's zero anywhere, then the derivative is `0`, and so it is a zero constant.

So this means `p(0) = t`, and `t` is not `0`.
You can divide by a any number that is not `0`,
and derivatives are linear.
The function `e(x) = p(x)/t` also solves the original differential equation,
and is `e(0)=1`.
The equation is position-independent, so `e(x+c)` is also a solution
for each `c`.
Since differential equations have unique solutions with the same starting conditions,
`e(x+c)/e(c)=e(x)`.
In other words, `e(x+c)=e(x)*e(c)` for every `x` and `c`.

With induction, `e(n)=e(1) ** n`.
More, `e(n/m) ** m = e(n/m * m) = e(n) = e(1) ** n`.
Taking out `m`th roots,

.. code::

    e(n/m) = rt_m(e(1) ** n)

If we just write ``e`` for ``e(1)``, we get


.. code::

    e(r) = e ** r

Since ``e' = e``,
we have ``e'' = e`` and so on.
In other words, every derivative at ``0`` is ``1``.
So the Taylor series looks like

.. code::

    e(x) = 1 + x/1! + x**2/2! + ...

Since this converges absolutely, it converges when ``x`` is a complex number as
well, and the differential equation still holds.

If ``t`` is real,

.. code::

    Re e(it) = 1 - t ** 2/2! + t ** 4/4! - ...
    Im e(it) = t - t ** 3/3! + t ** 5/5! - ...

Because of that

.. code:

    e(-i * t) = Re e(it) - i * Im e(i * t)

so

.. code::

    1 = e(0) = e(i*t - i*t) = e(i*t) * e(-i * t) = Re e(it) ** 2 + Im e(it) ** 2

In other words, if ``t`` is real,

.. code::

    ||e(i*t)|| = 1

In other words, ``e(i * t)`` is a function from the real line to the unit circle.

.. code::

   Re e(2 * i) < 0

from a quick estimation.
So there's a smallest number, q,

.. code::

   Re e(i * q) = 0

and because of that

.. code::

   Im e(i * q) = +/- 1


In other words,

.. code::

    e(i * q) = i
    e(i * 4 * q) = i**4 = 1 = e(0)

Let's call ``t = q * 4``, we have

.. code::

    e(x + i * t) = e(x) * e(i * t) = e(x)

So ``e`` is periodic, with a period of ``i * t``.
Pi is just ``t / 2``.

In this argument, the function ``e`` does all the hard work.
Pi just falls out of it as the period along the imaginary axis.
Pi can't find ``e``, but ``e`` can find Pi.

Pi is not wrong because it's half of Tau.
Pi is wrong because it's a property of ``e``,
not the other way around.

Next time you want to memorize a number, memorize ``e``.
