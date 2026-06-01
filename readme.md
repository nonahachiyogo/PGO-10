Stream API Tasks
This project contains a series of Java exercises designed to practice the Java Stream API (Java 17+). The goal is to perform data filtering, transformation, and analysis on a set of order records using functional programming principles.

Features
Data Processing: Uses filter, map, flatMap, and sorted.

Aggregation: Employs Collectors for grouping, summing, and partitioning.

Statistics: Calculates metrics using DoubleSummaryStatistics.

Safety: Properly handles Optional and OptionalDouble to prevent errors.

Development Notes
Environment: Developed using Java 17+.

Version Control: All code changes were tracked and committed using the IntelliJ IDEA built-in Version Control tools rather than the Git Bash console, ensuring seamless integration between code changes and commit history.

Control Questions
Why does average() return OptionalDouble, while sum() returns a double?
sum() can safely return 0.0 for an empty stream. However, you cannot divide by zero to get an average. OptionalDouble forces you to handle the case where the stream is empty to avoid errors.

What is the difference between map and flatMap?

map: Transforms one element into one new element (1-to-1).

flatMap: Flattens nested collections (like a list of items inside an order) into a single stream of elements (1-to-many).

Why do we need to create a new stream from entrySet() after collect(groupingBy(...))?
groupingBy returns a Map, which is not a stream. We need to convert the Map's entries into a stream to perform further operations like sorting by value or limiting results.

What happens when we reuse a stream reference (calling .count() then .mapToDouble())?
It throws an IllegalStateException. Streams are "use-once"—once a terminal operation (like count) is called, the stream is closed and cannot be traversed again.

Why does a pipeline like filter(...).map(...) print nothing?
Because those are intermediate operations, which are lazy. Without a terminal operation (like collect() or forEach()), the stream never actually executes the data processing.
