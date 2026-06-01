# Stream API Tasks

This project contains a series of Java exercises designed to practice the Java Stream API (Java 17+). The goal is to perform data filtering, transformation, and analysis on a set of order records using functional programming principles.

## Features

- **Data Processing:** Uses `filter`, `map`, `flatMap`, and `sorted` to manipulate data streams.
- **Aggregation:** Employs `Collectors` for grouping, summing, and partitioning complex data sets.
- **Statistics:** Calculates metrics using `DoubleSummaryStatistics` for quick reporting.
- **Safety:** Properly handles `Optional` and `OptionalDouble` to prevent null pointer exceptions and handle empty result sets gracefully.

## Development Notes

- **Environment:** Developed using Java 17+.
- **Version Control:** All code changes were tracked and committed using the IntelliJ IDEA built-in Version Control tools rather than the Git Bash console, ensuring seamless integration between code changes and the project workflow.

## Control Questions

**Why does `average()` return `OptionalDouble`, while `sum()` returns a `double`?**  
`sum()` can safely return `0.0` for an empty stream. However, you cannot divide by zero to get an average. `OptionalDouble` forces you to handle the case where the stream is empty to avoid errors.

**What is the difference between `map` and `flatMap`?**  
`map` performs a 1-to-1 transformation, while `flatMap` flattens nested collections (like lists within orders) into a single continuous stream of elements.

**Why do we need to create a new stream from `entrySet()` after `collect(groupingBy(...))`?**  
`groupingBy` returns a `Map`, which is not a stream. We must convert the Map entries back into a stream to perform further operations like sorting or limiting.

**What happens when we reuse a stream reference (calling `.count()` then `.mapToDouble()`)?**  
It throws an `IllegalStateException`. Streams are "use-once" — once a terminal operation is called, the stream is closed.

**Why does a pipeline like `filter(...).map(...)` print nothing?**  
These are intermediate operations, which are lazy. Without a terminal operation (like `collect()` or `forEach()`), the stream never executes the data processing.
