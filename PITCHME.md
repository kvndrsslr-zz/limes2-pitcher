# LIMES Issues and Solutions
<!-- page_number: true -->

---
## Common Problems
@ul

* massive code duplication
* violation of SRP
* violation of encapsulation
* improper use of abstract classes
* procedural coding style
* dead code (a lot)
* lack of refactoring / cleaning up code after research is finished

@ulend
---

### A case for good code in research

* common argument: we are data scientists, not software engineers
* but good coding practices will eventually also help research

+++

#### For the Community

* the research community will read and use our code in order  to reproduce paper results -> bad code quality likely to impair reputation
* partners / collaborators of funded projects in the industry will use or collaborate on our code -> good code leads to better relationships and less frustration

+++

#### For Ourselves

* code we develop today is part of our toolset tomorrow 
	* sound api design and clean, understandable code will boost productivity
	* -> more time to write great papers


---

## General Guidelines

+++

#### Interfaces

* most interfaces too bloated
* break them down into multiple smaller interfaces (SRP)
* improved modularity, less coupling between packages

+++

#### Classes

* minimize public interfaces
* don't code against implementations
* use abstract classes only for encapsulating common logic of subclasses
* abstract classes should be package-private
* don't hesitate to finalize methods in abstract classes 

+++

#### Modularity

* meaningful packages
* multi module maven project
* plugin architecture
* wrap third party libraries to reduce migration pain (example: jena)

+++

#### Testing

* unit tests should test *one unit* of code
* dependencies should be mocked
* don't duplicate logic between implementation and tests

---

## Ideas for LIMES 2.0

+++

#### Some general points

* use dependency injection (Dagger 2?)
* use plugin architecture (PF4J)
* increase test quality with automated mocking (Mockito)

+++

#### LIMES Configuration

* single standard: rdf configuration
* homogenous way to declare and parametrize all components
* rethink querying data
* rethink preprocessing declaration
* rethink LS declarations
* rethink automatic evaluation


+++

#### Core Components: Caches

* allow better programmatic access to graph structure
* use Jena Models under the hood?

+++

#### Core Components: Mapper / Measure

* Mapper / Measure interfaces fail to abstract over all implementations
* this defeats the purpose of those interfaces
* in turn, sub interfaces have been introduced
                * adds further complexity to instance creation
                * barriers for ml algorithms
* very problematic: graph similarity measures
                * need good programmatic access to graph structure
	        * default data pipeline (readers->caches) removes / makes it hard to access graph structure

+++

#### Spark / Flink Questions
* Try to reduce Spark/Flink-specific codebase
* Testing Spark/Flink?
* DI for Spark/Flink?
* Data flow in Spark/Flink?
* Architecture with Spark/Flink?
* Rewriting/ExecutionEngines for Spark/Flink?

