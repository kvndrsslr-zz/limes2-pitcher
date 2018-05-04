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
* a lot of dead code
* lack of good refactoring / cleaning up code 

@ulend
---

### A case for coding in research

* common argument: we do research not software developement
* but good coding practices will eventually also help research

+++

### A case for coding in research 

@ul

* the research community will read and use our code in order  to reproduce paper results -> bad code quality likely to impair reputation
* partners / collaborators of funded projects in the industry will use or collaborate on our code -> good code leads to better relationships and less frustration
* code we develop today is part of our toolset tomorrow 
	* sound api design and clean, understandable code will boost productivity
	* -> more time to write great papers

@ulend

---

## Specific problem areas

+++

### Testing 
* JUnit
	* Split unit and integration tests
* Mockito
	* Use for unit tests
* Goal: Increase test coverage & quality
	* Develop from scratch  with TDD?
	* Pair programming / Independent test developers?

+++

### Modular Design
* rethink package structure
* multilayered design?
* decouple from 3rd party libraries using wrappers?
* obey LoD?

+++

### Evaluation Package
* Goal? -> automate experiment implementations
* Goal achievable in general?
	* Current design (e.g. ML) often stands in the way of experiments
	* experienced the need of dirty unchecked casts and other hacks in order to perform experiments
	* with DI and proper implementation of SRP, information hiding, etc. it should be doable elegantly
	
+++

### Machine Learning
* current design too restrictive / does not allow for easy interaction 

+++

### Single Configuration Standard RDF
* We're experts at parsing, storing and processing graphs.
* XML is not easier to write or read than Turtle.
* Even if XML configuration is required for some reason, we have RDF/XML.

+++

### Mappers / Measures / Caches
* The Mappers/Measures interfaces fail to abstract over all possible implementations
* In turn, sub interfaces have been introduced
	* just adds complexity to instance creation
	* barriers for ml algorithms
* Most problematic: graph similarity measures
	* need good programmatic access to graph structure
	* our default data pipeline (readers->caches) removes graph structure / makes it very hard to access graph structure

+++

### Spark / Flink specific
* Testing Spark?
* DI with Spark?
* Data flow with Spark?
* Architecture with Spark?
* Rewriting/ExecutionEngines with Spark?
