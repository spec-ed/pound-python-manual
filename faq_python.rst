Frequently Asked Python Questions
=================================

Listed, in no particular order, are some of the questions and answers that come
up in #python frequently.

Flatten a Nested List
*********************

    I have a list of lists `[[a, b, c], [d, e, f]]` and I want to flatten it so
    its `[a, b, c, d, e, f]`.  How do you do that?

The user usually is dealing with data that is coming from some outside source,
like a database or a CSV file.  There are a number of answers for this on Stack
Overflow that mess with list comprehensions and other foolishness.  This has
been something in the standard library for quite a while, and got even easier
in 2.6.

The `itertools` module has a callable named `itertools.chain`.  This callable
takes, as positional arguments, iterables to yield values from sequentially.
The `itertools.chain.from_iterable` classmethod makes it even easier, by
accepting an iterable of iterables.

.. code-block:: python

   import itertools


   nested = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

   # In python versions 2.3 to 2.5
   flat = itertools.chain(*nested)

   # In python versions 2.6 and on (incl. 3)
   flat = itertools.chain.from_iterable(nested)

Splitting a list into groups of length N
****************************************

    I have a list of numbers `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, ...]` that I want
    to split into a list of lists, 5 items long, so it looks like `[[1, 2, 3,
    4, 5], [6, 7, 8, 9, 10], ...]`.  How do you do that?

.. code-block:: python

   flat = range(1, 11)
   nested = zip(*[iter(flat)] * 5)

If you look at that and think "Uh... What?", you would not be alone.  That is
an idiom that many Python programmers take for granted.  It isn't the best
looking code either.  Lets break it down.

.. code-block:: python

   # A list of numbers, 1 - 10.  Anything iterable would work.
   flat = range(1, 11)

   # gives us an object that will give you the next item in a sequence when
   # iterated over
   flat_iter = iter(flat)

   # lets put that inside a list...
   list_of_flat_iter = [flat_iter]

   # now we want the list the length of one group.  Multiplying a list by an
   # integer copies the list that many times.  `flat_iters` points to a list
   # that looks like `[flat_iter, flat_iter, flat_iter, flat_iter, flat_iter]`
   # Keep in mind, this is the same object in the list 5 times.
   flat_iters = list_of_flat_iter * 5

   # this is a little bit of magic now.  From the documentation of zip:
   #
   #     This function returns a list of tuples, where the i-th tuple contains
   #     the i-th element from each of the argument sequences or iterables.
   #
   # zip expects each iterable it works on to be passed as a positional
   # argument.  We now have a list (flat_iters) that contains the same iterator
   # over our list (flat) 5 times, since that is the length out the output
   # tuple we want.  We use argument unpacking on this list to pass the
   # iterator to zip 5 times.  With each pass zip makes, the iterator gives zip
   # the next 5 values from our input list (flat).
   nested = zip(*flat_iters)

The idiom has a notable drawback.  zip stops iterating at the end of the
shortest iterable, meaning, if your list is not divisible by the length of your
group, you will be one grouping short.  To solve this, instead of zip, use
`itertools.izip_longest
<https://docs.python.org/2.7/library/itertools.html#itertools.izip_longest>`_.
