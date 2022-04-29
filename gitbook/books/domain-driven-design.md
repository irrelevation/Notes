# Domain Driven Design

Excellent book centering around the thesis that designing, writing and analysing software should be an iterative process in wich a **[common language](#ubiquitous-language)**, a [model](#the-model) and the softweare itself mutually refine each other.

## Ubiquitous Language

A language that is developed and shared by all stakeholders. It is used to create and implement [the model](#the-model).

## The Model

The model should make those aspects of our domain explicit that are necessary to solve the problem and leave out those that are not.
The model must be coupled to it's implementation.
Developing the model is an iterative Process. The implementation will influence the model and vice versa.

### Associations

Keep associations to a minimum to reduce complexity (as few as possible, as many as necessary).
Eliminate bidirectional associations between [value objects](#value-objects).

### Entities

We care about entities because of _who_ or _which_ they are.
Their properties can vary between contexts or over time.
Identity is usually implemented via IDs.

### Value Objects

> These are the objects that describe things.

Value o bjects are identified by their qualia.
We care about them because of _what_ they are.
Value objects can be shared either by making them immutable and sharing the reference or by sharing a copy.
What is a value object in one context can be an entity in another.

### Services

> ... operations that do not conceptually belong to any object.

Services are defined by their actions.
They **are stateless**, i.e. instance of a service don't change their behaviour over time and different instances behave identical.
If an objects name contains "manager" or "service" you are probably dealing with a service.

### Modules

Modules are the chapters of your system's story.
They aim to reduce cognitive load by bundling code with high cohesion (technical _& conceptual_) and seperating code with low cognitive coupling (technical _& conceptual_).
We should refactor modules just like we do with code to adapt to changes in the model.

> Like everything else in domain-driven design, MODULES are a _communications mechanism_.

### Domain Object Life Cycle

#### Aggregates

Aggregates group objects to enforce invariants and consistency. Each aggregate has a **root**, i.e. an [entity](#entities) that you can reference to use the aggregate and it's constituents. You are not allowed to hold reference to the parts itself.

#### Factories

Factories enforce the invariants of object/aggregate creation and reconstitution.
They abstract complex object/aggregate creation and decouple it from those objects/aggregates and their clients.

#### Repositories

Repositories handle transition of objects/aggregates to and from **storage**.
They encapsulate the technology of data storage, retrieval and query, allowing us to deal with concepts of the domain model rather than the underlying infrastructure.

### Other Domain Concepts

#### Constraints

Make constrains explicit. If all data needed to evaluate the constraint resides in an object, make the constraint a method of that object. Otherwise seperate it into it's own object.

#### Processes

Make processes explicit only if the play an explicit role in the domain, not just because they are a byproduct.
Focusing on the aims rather than the _how_.
If you need to make them first class citizens of your model, they should be properly abstracted.
They can be expressed in [services](#services) or **strategies**.

## Design Patterns

### Specifications

A specification is an object that encapsulates one or more rules.
It is modeled after a predicate (as in predicate logic).
It takes one or more objects (depending on the arity of the predicate) and **tests** wether the criteria of the predicate are fulfilled.

### Assertions

Seperate queries (pure functions wich return values) from commands (functions wich mutate observable state).
Make the **side effects** of your commands explicit.
Use assertions to verify **preconditions**, **invariants** and **post-conditions** (see [design by contract](https://en.wikipedia.org/wiki/Design_by_contract#Bibliography) for more infos).
If your language doesn't natively support these constructs, use unit tests.^

### Closure Of Operations

> ... an operation whose return type is the same as the type of its argument(s).

If functions and methods are "closed under a type" they have less dependencies.
They introduce less mental overhead and are easier to reuse and compose.
An example would be JavaScripts `Array.prototype.filter()` method.

## Analysis Patterns

## Bounded Contexts

A domain model is only valid within a bounded context.
Ideally you want to maintain a single domain model shared by everyone.
But that is often not possible.
In case of multiple bounded contexts maintain a **context map**.
Clearly define the relationship between bounded contexts.
Bounded contexts often map to teams.

### Shared Kernel

Two bounded contexts share a kernel. They are highly coupled in both directions.
Frequent integration is key.

### Consumer/Supplier

A (mostly) one way dependency.
Be mindful of power relationships. Suppliers should serve customers.
Coordinate in short frequent intervals.
Clearly define interfaces and create automated acceptance testing to ensure you don't break the consumer.

### Conformist

Adhering to the upstream model simplifies translation.
It is an option for one way dependencies where the upstream team has no interest in _serving_ the downstream team (eg. large organisations or cross organisation).

## Anticorruption Layer

## Citation

Evans, E. (2004). Domain-driven design: Tackling complexity in the heart of software. Boston: Addison-Wesley.
