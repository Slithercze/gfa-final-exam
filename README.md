# Endpoint

## HTTP Request Communication Flow:
- The browser/client makes an HTTP request to a server. This travels through several layers (from application to physical). The server processes the request, and sends back a response, which goes through the layers back to the client.

### Create an HTTP request:
- **JavaScript**: Use `fetch()` or `XMLHttpRequest`.
- **Spring**: It handles incoming requests through controller methods annotated with `@RequestMapping` or specific annotations like `@GetMapping` and `@PostMapping`.

### Recognize a REST endpoint (stateless/resource):
- **Stateless**: The server doesn't store client state between requests.
- **Resource-oriented**: Endpoints represent resources, e.g., `/users` for user resources.

### Send or receive data in body or URL params:
- **JavaScript**: Use the `body` property in `fetch` for POST requests. Use URL for GET parameters.
- **Spring**: `@RequestBody` for body data, `@RequestParam` for URL parameters.

### Different parts of a URL:
- **Protocol**: `http`
- **Domain**: `example.com`
- **Path**: `/users`
- **Query parameters**: `?id=1`

### Common HTTP status codes:
- 200 OK
- 201 Created
- 400 Bad Request
- 401 Unauthorized
- 404 Not Found
- 500 Internal Server Error

# Authentication

## Aim of authentication and authorization:
- **Authentication**: Verifies who a user is.
- **Authorization**: Determines what a user can do.

## Token-based authentication flow:
- User logs in, server returns a token (e.g., JWT). Subsequent requests include this token for authentication.

## Token vs. session-based authentication:
- **Token**: Stateless, scales better, typically used with RESTful APIs.
- **Session**: Server stores session data between requests, doesn't scale as easily.

# Data Flow

## Identify separate responsibilities:
- Following MVC: Controllers handle HTTP requests, Services manage business logic, Repositories handle data operations.

## Flow of data:
- JavaScript fetches data from Spring API -> Spring controller accepts the request -> Service processes -> Repository interacts with database -> Data returns through the layers back to JavaScript.

## Server-side vs. client-side rendering:
- **Server-side**: Spring returns fully formed HTML (like with Thymeleaf).
- **Client-side**: JavaScript updates the DOM dynamically with data from the server.

## Dependency injection:
- Spring's core feature. It injects objects dependencies from outside the class, promoting loose coupling.

# Testing

## Reason for Testing:
- Testing ensures that the software works as expected and helps in identifying defects. It provides confidence in the software's reliability, boosts development speed by catching issues early, and aids in maintaining code quality during subsequent changes.

## Difference between Unit and Integration Tests:
- **Unit Tests**: Focus on individual units/components of the software without external interactions. They are used to ensure that individual functions/methods/classes work as expected.
- **Integration Tests**: Ensure different components or systems work together. They focus on the interaction between units or systems like databases.

## Advantages and Disadvantages of Unit and Integration Tests:
- **Unit Tests**:
    - *Advantages*: Fast, pinpoint exact issues, test units in isolation.
    - *Disadvantages*: Might not catch interaction-based issues.
- **Integration Tests**:
    - *Advantages*: Identify interaction-based issues.
    - *Disadvantages*: Slower, might not pinpoint exact issue location.

## Mocking in Testing:
- **Reason for Mocking**: Mocking simulates the behavior of real objects, helping in isolating the unit of code from external dependencies, simulating various scenarios, and speeding up tests.

# Database (DB)

## Data Modeling in DB:
- Data in relational databases is modeled using tables with columns representing attributes. Rows represent individual instances.

## CRUD Operations:
- **Create**: `INSERT INTO table_name (...) VALUES (...);`
- **Read**: `SELECT ... FROM table_name WHERE ...;`
- **Update**: `UPDATE table_name SET ... WHERE ...;`
- **Delete**: `DELETE FROM table_name WHERE ...;`

## Model Relations in DB:
- In relational databases, models are related using primary and foreign keys. These keys form relationships like one-to-one, one-to-many, and many-to-many.

# Refactoring

## Refactor Goals:
- The primary goal is to improve code readability, maintainability, and sometimes performance without changing external behavior.

## Code Smells:
- Long methods.
- Large classes.
- Duplicated code.
- Dead code.
- Magic numbers.

## Style Guides and Linters:
- They ensure code consistency, making it readable and maintainable. Linters can catch and sometimes fix coding issues automatically.

## Reduce complexity of method:
- Reduce method complexity by breaking it into smaller functions, avoiding nested loops, simplifying conditions, and using clear naming.

# Object-Oriented Programming (OOP)

## Class vs. Instance:
- **Class**: A blueprint for objects.
- **Instance**: An object created from a class blueprint.
- **Constructors**: Special methods to initialize new objects.

## Inheritance in OOP:
- Used when there's a clear "is-a" relationship, e.g., "Car is a Vehicle".

## Encapsulation in OOP:
- Bundling data and methods into a single unit and restricting external access.

## Interfaces vs. Abstract Classes:
- **Interfaces**: Define contracts classes must follow.
- **Abstract Classes**: Provide base classes with default behavior.

# Development Operations

## Merge Conflicts:
- Occur when changes in different branches overlap. Resolved manually.

## Version Control Workflow:
- Collaborators create branches, make commits, then merge them into the main branch.

## Releasing Code to Production:
- Code is moved from development to staging/testing, then to production.

## Application Configuration:
- Different configurations are set up for development, staging, and production environments.

# Error Handling

## Stack Trace:
- Shows the call stack when an exception occurs. Look for line numbers, method names, and file names.

## Runtime vs. Compile-time Errors:
- **Compile-time**: Detected by the compiler.
- **Runtime**: Occur during program execution.

## Error Handling in Java Spring:
- Use `@ControllerAdvice` and `@ExceptionHandler` for specific exception types.

## Data/Input Validation:
- Validates data at the entry point, ensuring data integrity and reducing risks.

## Debugging Process:
1. Identify the Issue.
2. Isolate the Source.
3. Inspect Variables and Flow.
4. Formulate a Hypothesis.
5. Test the Hypothesis.
6. Fix and Verify.
7. Reflect and Learn.

