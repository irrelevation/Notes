# Testing

## Acceptance Tests
Acceptance Tests focus on _what_ a system does (compared to _how_ it does it).
They are written from a users perspective and you usually start with a user story.

### 4 Layer Approach
This apprach provides a very high level of abstraction.


1. **Test Cases** - written in the language of your problem domain, talking about _what_ you wan't to do
2. **DSL** - an (internal) domain specific language written in the language of your problem domain, allows us to write tests quickly and efficiently
3. **Protocol Driver** - translates your DSL to your the language of your system, isolates the _how_
4. **System under Test**

## Resources
[Excellent Software Testing](https://ingophilipp.medium.com/excellent-software-testing-6e0fd8f3e11e)
