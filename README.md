Objective
Implement a bookstore REST API using Java and Spring.

Background
* Self-publish their adventures.
* Sell their books online to other Wookies.
* Donate the profits to buy medical supplies for an impoverished Ewok settlement.

Recommended Technology Stack
Use Spring Boot with:

* Spring Web for REST controllers.
* Spring Security for authentication and authorization.
* Spring Data JPA or JDBC for persistence.
* Hibernate Validator (jakarta.validation) for request validation.

Bootstrap the project using Spring Initializr with Maven or Gradle.

Use the following package structure:
* controller: REST endpoints.
* service: Business logic and authorization checks.
* repository: Data access.
* model or entity: Persistent entities.
* dto: Request and response payloads.
* config: Security, serialization, and content negotiation.

Follow these naming conventions:
* Classes: PascalCase, such as Book, AppUser, and BookController.
* Fields and methods: camelCase, such as authorPseudonym and unpublishBook.

Implementation Requirements
Response Formats
* Support JSON and XML responses based on the Content-Type header, as required by the assignment.
* Account for Spring’s typical use of the Accept header and produces for response content negotiation.
* Configure JSON and XML message converters, such as Jackson and Jackson XML.

User Model
* Create a custom user model that includes an author pseudonym field, such as * authorPseudonym.
* Integrate the user model with Spring Security by implementing UserDetails or using a custom UserDetailsService.

Book Model
* Create a book model with the following fields:
    * Title.
    * Description.
    * Author, linked to the custom user model.
    * Cover image.
    * Price.

* Choose appropriate data types for each field.

* If using JPA, consider a @ManyToOne relationship between a book and its author.

Authentication
* Provide an authentication endpoint that:
    * Accepts a username and password.
    * Returns a JSON Web Token (JWT) upon successful authentication.

* Use stateless JWT authentication.
* Hash passwords using BCryptPasswordEncoder.
* Use a JWT library such as jjwt.

Public Book Endpoints
* Expose the /books resource without requiring authentication.
* Allow only GET operations on this public resource:
    * List books.
    * Retrieve an individual book.
* Make the book list searchable through query parameters.
* Implement filtering using repository queries or Spring Data specifications.

Authenticated User Resources
* Provide REST resources for authenticated users.
* Implement standard CRUD operations for these resources.
* Provide a DELETE endpoint to unpublish a book.
* Enforce ownership checks in the service layer so users can unpublish only their own books.

API Testing
* Write API tests for every implemented endpoint.
* Use JUnit 5 and spring-boot-starter-test.
* Use MockMvc, or WebTestClient if using WebFlux.
* Consider:
    * H2 as a test database.
    * Testcontainers for more realistic integration tests.

* Include tests verifying that users cannot unpublish books belonging to other authors.

Evaluation Criteria
* Follow framework and API development best practices.
* Maintain clear separation between controllers, services, and repositories.
* Use DTOs for API request and response payloads.
* Configure security explicitly.
* Provide API tests for all implemented endpoints.
* Ensure users can unpublish only their own books.