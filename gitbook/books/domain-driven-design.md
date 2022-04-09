# Domain Driven Design

Excellent book centering around the thesis that the way we analyse and design software systems should be guided by a **[common language](#ubiquitous-language)**.

## Ubiquitous Language

A language that is developed and shared by all stakeholders. It is used to create and implement [the model](#the-model).

## The Model

The model should model those aspects of our domain that are necessary to solve the problem and leave out those that are not.
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

## Citation

Evans, E. (2004). Domain-driven design: Tackling complexity in the heart of software. Boston: Addison-Wesley.
