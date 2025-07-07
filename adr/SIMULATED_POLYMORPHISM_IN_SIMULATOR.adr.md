# Acceptance of code smell "Simulated Polymorphism" in SimulatorSession

## Decision
It is accepted to "simulate polymorphism" in the implementation of the `SimulatorSession`s to implement simulation of each SQL construct.

### Explanation 
In `SimulatorSession`s used for unit-testing we "simulate polymorphism" of the SQL language constructs, i.e. checking its type and simulating its behaviour using `if`- or `when`-statements.
In general, this is a well known code smell.

However, it is accepted here, because it allows to keep the simulation out of the SQL model (where it would be implemented with real polymorphism) and thereby in the production code.

Furthermore, when using "real" polymorphism, simulation of specific behaviour of a certain SQL engine would be implemented in a subclass of the language construct.
As long as its SQL syntax stays the same, users would not be forced to use the engine-specific subclass and might forget it.
Hence, in tests they would not get the right engine-specific behaviour.

Note: The [Visitor Pattern](https://en.wikipedia.org/wiki/Visitor_pattern) could have been an option and was tried first.
But while the visitor generating the SQL string could simply return `String`, the visitor generating the simulation of a `Expression<E : Engine<E>, T>` (with `T` being its return type) would have to return a `(Row) -> T`, i.e. with a varying `T` depending on the expression.
Such a nested generic is not possible to define as the visitor's signature.

### Comparison of alternatives
|                                        | "real" polymorphism                                            | *simulated polymorphism*                     | Visitor Pattern                  |
|----------------------------------------|----------------------------------------------------------------|----------------------------------------------|----------------------------------|
| separation of simulation from real SQL | :-1: simulation logic in production classes                    | :+1: simulation separate in SimulatorSession | :+1: separate simulation visitor |
| clean OO design                        | :+1: that's how OO is meant                                    | :-1: code smell                              | :shrug: clean, but complex       |
| does the job                           | :warning: would not enforce engine specific behaviour in tests | :+1: yes                                     | :boom: not feasible              |                                   
