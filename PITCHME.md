# LIMES Issues and Solutions
<!-- page_number: true -->

---
## Common Problems
* massive code duplication!
* violation of SRP
* violation of encapsulation
* improper use of abstract classes where interfaces should be used
* procedural coding style
* a lot of dead code, as a result of the lack of good refactoring / cleaning up code after a given research question has been answered and enough data has been gathered for the paper. true, we're researchers, not engineers but imho, our software deserves more devotion for three reasons:

### A case for coding in research

1) the community will eventually look up and use our code when trying to reproduce our published research results. bad code will probably result in a drop in reputation
2) partners / collaborators of funded projects in the industry will get in touch with our code. good code will lead to good relationships and less frustration.
3) last but not least, the code we develop today is part of the tool we use tomorrow: a sound api design and clean, understandable code will boost productivity when implementing new ideas and, in turn create more time to focus on writing great papers.

## Specific problem areas

### Testing 
* JUnit
	* Split unit and integration tests
* Mockito
	* Use for unit tests
* Goal: Increase test coverage & quality
	* Develop from scratch  with TDD?
	* Pair programming / Independent test developers?

### Modular Design
* rethink package structure
* multilayered design?
* decouple from 3rd party libraries using wrappers?
* obey LoD?

### Evaluation Package
* Goal? -> automate experiment implementations
* Goal achievable in general?
	* Current design (e.g. ML) often stands in the way of experiments
	* experienced the need of dirty unchecked casts and other hacks in order to perform experiments
	* with DI and proper implementation of SRP, information hiding, etc. it should be doable elegantly

### Machine Learning
* current design too restrictive / does not allow for easy interaction 

### Single Configuration Standard RDF
* We're experts at parsing, storing and processing graphs.
* XML is not easier to write or read than Turtle.
* Even if XML configuration is required for some reason, we have RDF/XML.

### Mappers / Measures / Caches
* The Mappers/Measures interfaces fail to abstract over all possible implementations
* In turn, sub interfaces have been introduced
	* just adds complexity to instance creation
	* barriers for ml algorithms
* Most problematic: graph similarity measures
	* need good programmatic access to graph structure
	* our default data pipeline (readers->caches) removes graph structure / makes it very hard to access graph structure

### Spark / Flink specific
* Testing Spark?
* DI with Spark?
* Data flow with Spark?
* Architecture with Spark?
* Rewriting/ExecutionEngines with Spark?



#dice/limes