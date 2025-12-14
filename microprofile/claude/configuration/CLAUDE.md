## Logging
- For Java projects: use java.lang.System.Logger instead of System.out statements
- Never use java.util.logging.Logger

use Java SE APIs over writing custom code.
use Java 25
write modern Java syntax (var, pattern matching)
write simple, undertandable and beautiful Java code
do not write obvious JavaDoc comments
structure the code using the Boundary Control Entity (BCE/ECB) pattern
name packages after their domain responsibilities
create package-info.java for top level packages and write JavaDoc to document the design decisions, intentions and code responsibilities. Capture the package responsibility and not the contents. Do not explain the ECB pattern, focus on domain logic.
follow the links in JavaDoc to external specifications and use them for code generation
keep coarse-grained classes in the boundary package
implement procedural business logic in the control package.
maintain domain objects, data classes, and entities in the "entity" package
name classes after their responsibilities
prefer unchecked over checked exceptions
do not throw generic checked exceptions like e.g. java.lang.Exception
prefer interfaces with static methods over classes in the control package for stateless / procedural logic
avoid using final, prefer clean code
avoid private visibility
unit test methods must not start with "test"
avoid writing repetitive unit tests. Keep only essential tests that verify core functionality without redundancy.
in utility interfaces prefer static over default methods
integration tests end with IT and are executed by the failsafe maven plugin. There is no configuration necessary
always ask before you change the pom.xml
use assertj library instead of jupiter
prefer factory methods in records over passing null in constructors
write brief and clear README.md files.
prefer multiline Strings over String concatenations
Only use interfaces with multiple implementations.
avoid using meaningless endings like: *Impl, *Service or *Manager for class names. Name classes after their responsibilities.
according to "Maximal Cohesion, Minimal Coupling" create smaller classes with dedicated responsibilities
keep methods short and testable
prefer the java.util.stream.Stream API over for loops. 
prioritize brevity and expresiveness
do not rephrase code in javadoc. Either describe the "why" or do not comment at all
document the intentions in JavaDoc.
do not explain the BCE pattern
do not repeat the boundary, control, entity names in package-info.java javadoc
do not use final for fields
do not use Java interface with abstract methods only which are implemented by a single implementation. Use classes directly.
use interfaces for the implementation of the strategy only. prefer simple code.
prefer List.of over String[]

## Package Naming Conventions
- Always create application level package with the name derived from the maven project or context. Use descriptive, domain-related names.
- create packages representing business components named after their responsibilities. e.g. [ORGANIZATION_NAME].[APP_NAME].[COMPONENT_NAME].[boundary|control|entity]
- create custom exceptions only with significant added value
do not use reactive API, prefer virtual threads


## Code Style
- Do not create multiline lambda expressions. Use method references instead.
- avoid forEach. Prefer java.util.stream.Stream methods.
- class names must not end with "Control"
- stacks should end with "Stack" suffix


## Documentation
- Write brief, 'to the point' README.md files. These should be helpful for advanced developers.
- use precise and concise language in the documentation
- use popular, also funny, technical terms from the Java SE, MicroProfile and Jakarta EE ecosystems as examples in unit test and javadoc.
- do not write trivial unit tests
- prefer Stream.of to Arrays.stream
- classes with cross-cutting functionality are located in the root application package
- prefer toList() to .collect(Collectors.toList())
- do not generate code initially in an empty project
- use Java SE APIs over writing custom code.
- prefer import statements over fully qualified class names
- do not rephrase simple code as javadoc within method bodies
- reuse the enum constants as values if possible
- enum constants do not have to follow the naming conventions
- use the most recent Java 25 APIs

## Package Structure Principles
- the top level package in ECB / BCE reflects the responsibility of the application or it is the application name
- Children of the top level ECB / BCE package are called business components and are named after their responsibilities
- the first package in BCE structure is the organization or project name, e.g. "airhacks". It is the namespace.
- the package structure is [ORGANIZATION_NAME].[PROJECT_NAME].[COMPONENT_NAME].[boundary|control|entity]


## General Best Practices
- use Text Blocks instead of regular String when it makes the code more readable
- Do not rephrase already existing information from the source code in JavaDoc
- avoid using the suffix "Factory". Use only in case it is a Factory GoF pattern
- only use the suffix "Builder" for classes with typical builder structure like e.g. method chaining

## API Design
- prefer HttpApi over RestApi. Only use RestApi for features not available in HttpApi
- use asynchronous Http APIs like e.g.  HttpClient.sendAsync only if explicitly requested.
- prefer synchronous HTTPClient APIs


## Project Management
- do not edit pom.xml without asking

## Class Naming Conventions
- classes must not end with "Creator". You can use plural instead.
- infrastructural classes must not end with "Manager"

## README Guidelines
- do not include detailed project structure (file/folder listings) in README files. High-level module descriptions are acceptable.
- do not use private visibility in Tests
- always implement the simplest possible solution. Ask before implementing enhancements or optional features.


## Project Initialization
- do not create or change any files on opening in existing projects. Stop after initialization and wait for instructions.


## Naming Conventions
- only use the suffix "Resource" for JAX-RS classes and elements directly related to the "resource" domain.

## Java Code Design
- consider using Java records instead of using Java classes with final fields
- do not mark class fields as private and final. Just use the package-private visibility instead.

## Code Visibility
- avoid "private static" methods. prefer default visibility
- Do not use the "Service" suffix. Name classes and elements after their responsibilities. Avoid generic names.
- avoid writing "getter" methods starting with "get"
- not every BCE component needs a dedicated boundary package. Contents of "control" package can be accessed directly by other components.

## Architectural Principles
- keep the design KISS and YAGNI
- do not create empty delegates which just call methods without any added value

## Assertion Best Practices
- the presence of isEqualTo assertion makes less specific checks like e.g. startsWith, isNotNull obsolete

## Coding Style
- prefer multiple simpler lines to one more complex line.

## Package Info Best Practices
- do not create package-info.java files for components with obvious meaning or trivial components. Describe the "Why?" and not the implementation details. Focus on the 'why' rather than the implementation details.

## JavaDoc Best Practices
- do not create single-lined JavaDoc comments which rephrase the code without adding any additional information

## Resource Management
- prefer try-with-resources over explicitly closing the resources

## Java Object Reference
- use reference instance fields with "this"
- do not use fully qualified annotation names. Use imports instead

## Testing
- create minimalistic tests first
- Do not write unit tests to verify implementations that cannot fail, such as enums, records, and getters and setters.
- prefer List.of over new ArrayList<>()
- never list REST resources in READMEs
- throw RuntimeException subclasses, not directly
- do not use "Orchestrates" term in documentation. Use more specific alternatives
- the boundary, control, entity packages are only allowed in business components
- the package containing the application only comprises business components. boundary, control and entity packages are not allowed.
- create well-named methods for coarse-grained, cohesive, self-contained logic to improve the readability of your code.
- create multiple classes only if it decreases the complexity and increases the readability
- create custom exceptions only if this significantly improves the robustness or maintainability
- Write simple code first. Always ask for the creation of extension points
- Never over-engineer the code. Ask about adding optional features.
- do not use the "get" convention. Prefer the record convention. e.g. configuration() instead of getConfiguration()
- do not use "simple", "lightweight" or other generic adjectives in the documentation. Be as specific and precise as possible.
- prefer variable declaration over lengthy method chaining
- prefer JSON-P over JSON-B
- do not implement business logic in JAX-RS resources, delegate instead
- place facades in the boundary package.
- prefer enums over plain Strings for finite, well-defined, values

## System Tests (ST)
- ST / System Tests are created in a dedicated Maven module ending with "-st"
- use microprofile-rest-client for testing JAX-RS resources
- REST client interfaces: src/main/java of the -st module (so they can be used by tests)
- Test classes: src/test/java of the -st module
- name client interfaces after the resource with "Client" suffix (e.g., GreetingsResource -> GreetingsResourceClient)
- RegisterRestClient configKey: "service_uri"
- STs end with "IT" suffix
- generate at most three UTs, ITs or STs

## JSON serialization with JSON-P
- record entities should ship with toJSON method which returns a JSON-P object
- always map JSON-P in the boundary to entities
- create the record entities from JSON-P JsonObject in the static method: fromJSON(JsonObject json)

- test methods must not start with "should"
- use lines with rounded style in draw.io diagrams
- use lines with rounded (not curved) style in draw.io diagrams
- create new components with minimal amount of business logic.
- create new components with entities only containing essential fields
- remove unused imports
- if there is not Boundary stereotype, use ApplicationScope instead
- prefer in resource to return JAX-RS response over JsonObject
- in unnamed classes do not import packages available in java.base module
- do not use static methods in unnamed classes
- Transactional is only allowed in boundary layer
- use import statements
- extract variable to eliminate duplication
- resources should be named in plural e.g. SpeakersResource not SpeakerResource
- inherit in JAX-RS projects from the WebApplicationException, or subclass, to get the proper status code
- model value objects as enums
- health checks has to be placed in the boundary package
- health checks must not start with "Service" and has to be named after their responsibilities
- do not create new "@RegisterRestClient(configKey," reuse existing
- never use constructor injection
- prefer AssertJ over JUnit assertions
- never use quarkus-hibernate-validator
- use explicit exceptions for BadRequestException for Response.Status.BAD_REQUEST
- do not re-throw expception with e.g. "throw e" without any adding value
- avoid creating unnecessary intermediate collections when streaming arrays
- always use web application exception in compact constructors in JAX-RS projects
- in case the modules are listed in the README.md, also provide links
- Extract repeated calculations or string concatenations into helper methods (DRY principle)
- Logger fields must be named LOGGER (uppercase) and marked as static final
- If a lambda requires multiple statements or braces {}, extract it into a well-named helper method instead.
- always maintain cognito functionality in a dedicated stack
- all stacks, except the application stack, have to be placed in boundary package
- keep stacks independent. Never pass them directly.
- prefer imports over fully qualified names. e.g. java.util.List should be imported
- "@Consumes" and "@Produces" in JAX-RS projects should be declared on class-level.
- Maven pom.xml must not be created for Java 25 CLI applications
- Java 25 CLI applications will be executed in source-file mode
- you must create metrics and observability features with OTEL.
- entities are maintaining state and the corresponding behavior