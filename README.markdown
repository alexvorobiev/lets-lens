# Let's Lens

![NICTA](http://i.imgur.com/sMXB9XB.jpg)

Let's Lens presents a series of exercises, in a similar format to
[the NICTA functional programming course material](http://github.com/NICTA/course).
The subject of the exercises is around the concept of lenses, initially proposed
by  Foster et al., to solve the view-update problem of relational databases.

The theories around lenses have been advanced significantly in recent years,
resulting in a library, implemented in Haskell, called `lens`.

http://hackage.haskell.org/package/lens

The exercises take into account various possible goals. For example, if you wish
to study the history of lenses, then build up to the most recent theories, it is
best to start at the `Lets.GetSetLens` module. If you wish to derive the
structure of lenses from first principles, then derive the more modern theories,
start at the `Lets.Lens` module.

Exercises can be recognised by filling in a function body that has a placeholder
of `error "todo: <function-name>"`.

----

### Running the tests (from NICTA course)

Some exercises include examples and properties, which appear in a comment above
the code for that exercise. Examples begin with `>>>` while properties begin
with `prop>`.

The solution to the exercise must satisfy these tests. You can check if you have
satisfied all tests with cabal-install and doctest. From the base directory of
this source code:

    > cabal update
    > cabal install cabal-install
    > cabal install --only-dependencies
    > cabal configure --enable-tests
    > cabal build
    > cabal test

Alternatively, you may run the tests in a single source file by using `doctest`
explicitly. From the base directory of this source code:

    > doctest -isrc -Wall -fno-warn-type-defaults <filename.hs>

Using stack:

    > stack exec doctest -- -isrc -Wall -fno-warn-type-defaults <filename.hs>
    
Note: There is a [bug in GHC 7.4.1](http://ghc.haskell.org/trac/ghc/ticket/5820)
where for some configurations, running the tests will cause an unjustified
compiler error.


### Exercise modules

##### `Lets.GetSetLens`

This module presents a series of exercises, representing lenses as a traditional
pair of "`get` and `set`" functions. This representation may be beneficial as it
easily appeals to an intuition of "what a lens is", however, it is outdated. 

These exercises are useful to gain an initial understanding of the problems that
lenses solve, as well as to gain an insight into the history of lenses and how
the theories have developed over time.

##### `Lets.StoreLens`

This series of exercises is similar to `Lets.GetSetLens`, however, using a
slightly altered representation of a lens, based on the `Store` comonad, which
fuses the typical `get` and `set` operations into a data structure. This
representation is described in detail in
*Morris, Tony. "Asymmetric Lenses in Scala." (2012).*

##### `Lets.OpticPolyLens`

This series of exercises introduces a new representation of lenses, first
described by Twan van Laarhoven. This representation also introduces a
generalisation of lenses to permit *polymorphic update* of structures.

##### `Lets.Lens`

This series of exercises starts at first principles to derive the concept of a
lens, as it was first described by Twan van Laarhoven. The derivation then goes
on to described other structures to solve various practical problems such as
*multi-update* and *partial update*.

This representation presents a generalisation, permitting *polymorphic update*
over structures. After lenses are derived, further concepts are introduced, such
as `Fold`s, `Traversal`s and `Prism`s.

----

### Credits

* Edward Kmett on the [derivation of lenses](https://github.com/ekmett/lens/wiki/Derivation)
