# Extra DSL layer on top of a precise and explicit SQL model

## Decision
At its core, **Kraft**SQL aims to model SQL precisely and explicitly, even if it's not convenient to write SQL statements with this implementation.
In addition there is a separate DSL layer on top.

### Explanation 
**Kraft**SQL promises coding support and bug detection for SQL at compile time, thanks to Kotlin and its strong type system.
This requires to model SQL very precisely in Kotlin.

With a concise language like Kotlin, we tried to offer a convenient API for writing SQL at the same time.
However, we have found that, due to the fundamental differences between SQL and Kotlin, this did not succeed.

Instead we want to separate concerns:
- A precise and explicit model of SQL to ensure correctness.
- A DSL and "syntactic sugar" on top for convenience.

### Comparison of alternatives
|                           | *separate SQL model and DSL* | explicit and convenient SQL implementation |
|---------------------------|------------------------------|--------------------------------------------|
| Implementation effort     | :-1: extra effort for DSL    | :+1: single, compact implementation        |
| Implementation complexity | :+1: separation of concerns  | :boom: didn't work                         |
