# 1. Endpoint

### Able to explain HTTP request communication flow
- The browser/client makes an HTTP request to a server. This travels through several layers (from application to physical). The server processes the request, and sends back a response, which goes through the layers back to the client.

### Able to demonstrate how to create an HTTP request
- **JavaScript**: Use `fetch()` or `XMLHttpRequest`.
- **Spring**: It handles incoming requests through controller methods annotated with `@RequestMapping` or specific annotations like `@GetMapping` and `@PostMapping`.
- **request** je methoda post get... nema status code
- **reponse** ma status code 200, 401 .., nemá metodu
- create http request: otevru browser, dam google a dam enter

### Able to recognize a REST endpoint (stateless/resource)
- **REST** = standart, ktery definuje jak nadesignovat endpoint, returns json
- **Stateless**: The server doesn't store client state between requests.
- **Resource-oriented**: Endpoints represent resources, e.g., `/users` for user resources.

### Able to send or receive data either in body or in URL params
- **JavaScript**: Use the `body` property in `fetch` for POST requests. Use URL for GET parameters.
- **Spring**: `@RequestBody` for body data, `@RequestParam` for URL parameters.
- put nahrazuje cely objekt,
- patch aktualizuje jen danou vlastnost objektu
- posíláme data v header, body, url dělíme => path variable, url parameters

### Able to identify the different parts of a URL
- **Protocol**: `http`
- **Domain**: `example.com`
- **Path**: `/users`
- **Query parameters**: `?id=1`
- **Fragment**: `#section`

### Able to describe the most common HTTP response status codes
- 200 OK
- 201 Created
- 400 Bad Request
- 401 Unauthorized
- 404 Not Found
- 500 Internal Server Error

# 2. Authentication

### Aim of authentication and authorization:
- **Authentication**: Verifies who a user is.
- **Authorization**: Determines what a user can do.

### Token-based authentication flow:
- User logs in, server returns a token (e.g., JWT). Subsequent requests include this token for authentication.

### Token vs. session-based authentication:
- **Token**: Stateless, stored client-side, scales better, typically used with RESTful APIs.
- **Session**: Server stores session data between requests, doesn't scale as easily.

# 3. Data Flow

### Identify separate responsibilities:
- Following MVC: Controllers handle HTTP requests, Services manage business logic, Repositories handle data operations.

### Flow of data:
- JavaScript fetches data from Spring API -> Spring controller accepts the request -> Service processes -> Repository interacts with database -> Data returns through the layers back to JavaScript.
- Popsat flow v naší aplikaci (nějakej endpoint)

### Server-side vs. client-side rendering:
- **Server-side**: Spring returns fully formed HTML (like with Thymeleaf).
- **Client-side**: JavaScript updates the DOM dynamically with data from the server.

### Dependency injection:
- Spring's core feature. It injects objects dependencies from outside the class, promoting loose coupling.
- 'Back in my days we called it "Passing arguments"'
- It's a fancy way to say passing arguments

# 4. Testing

### Reason for Testing:
- Testing ensures that the software works as expected and helps in identifying defects. It provides confidence in the software's reliability, boosts development speed by catching issues early, and aids in maintaining code quality during subsequent changes.

### Difference between Unit and Integration Tests:
- **Unit Tests**: Tests a single unit of code in isolation.
- **Integration Tests**: Tests the interaction between multiple units/modules.

### Advantages and Disadvantages of Unit and Integration Tests:
- **Unit Tests**:
    - *Advantages*: Fast, pinpoint exact issues, test units in isolation.
    - *Disadvantages*: Might not catch interaction-based issues.
- **Integration Tests**:
    - *Advantages*: Identify interaction-based issues.
    - *Disadvantages*: Slower, might not pinpoint exact issue location.
 
### Simple unit test: (napsat jednoduchý unit test na naše algo ve zkoušce)
- For a function that adds two numbers: ensure that passing 2 and 3 returns 5.
```java
@Test
public void testAddition() {
    Calculator calculator = new Calculator();
    assertEquals(5, calculator.add(2, 3));
}
```

### Write simple project specific test cases:  (napsat jednoduchý unit test v našem projektu)
- Let's consider a user service in a Spring project: 
```java
@Test
public void testRetrieveUserById() {
    User user = userService.getById(1L);
    assertNotNull(user);
    assertEquals("John", user.getName());
}
```


### Mocking in Testing:
- **Reason for Mocking**: Simulate behavior of real objects in unit tests. Avoids slow and uncontrollable factors like databases or APIs.

# 5. Database (DB)

### Data Modeling in DB:
- Data in relational databases is modeled using tables with columns representing attributes. Rows represent individual instances.
  
### Retrieve data from multiple tables using SQL:
- Using JOIN operations in SQL.
- For example: 
```sql 
SELECT * FROM books JOIN authors ON authors.id = books.author_id
```

### Common SQL aggregate functions:
- COUNT(), SUM(), AVG(), MAX(), MIN().
  ```sql 
  SELECT COUNT(*) FROM orders; -- Counts the total number of rows in the 'orders' table.
  SELECT SUM(amount) FROM orders; -- Calculates the sum of 'amount' values in the 'orders' table.
  SELECT AVG(amount) FROM orders; -- Calculates the average 'amount' value in the 'orders' table.
  SELECT MAX(amount) FROM orders; -- Retrieves the highest 'amount' value in the 'orders' table.
  SELECT MIN(amount) FROM orders; -- Retrieves the lowest 'amount' value in the 'orders' table.
  ```
  example: 
  ```sql 
  SELECT name, COUNT(books.id) FROM authors JOIN books ON authors.id = author_id GROUP BY authors.id, books.id
  ```


### CRUD Operations:
- **Create**: `INSERT INTO table_name (...) VALUES (...);`
 ```sql
INSERT INTO authors (name) VALUES ('name')
  ```
- **Read**: `SELECT ... FROM table_name WHERE ...;`
 ```sql
SELECT * FROM authors WHERE name = 'Miro';
  ```
- **Update**: `UPDATE table_name SET ... WHERE ...;`
```sql
UPDATE authors SET name = 'new name' WHERE id = 1;
  ```
- **Delete**: `DELETE FROM table_name WHERE ...;`
```sql
DELETE from authors WHERE id = 1;
  ```

### Model Relations in DB:
- In relational databases, models are related using primary and foreign keys. These keys form relationships like one-to-one, one-to-many, and many-to-many.

# 6. Refactoring

### Refactor Goals:
- The primary goal is to improve code readability, maintainability, and sometimes performance without changing external behavior.
- Úprava kódu bez změny funkcionality

### Code Smells:
- Long methods.
- Large classes.
- Duplicated code.
- Dead code.
- Magic numbers.

### Style Guides and Linters:
- They ensure code consistency, making it readable and maintainable. Linters can catch and sometimes fix coding issues automatically.
- Style guides and linters are essential for code quality and consistency.
- Style guides provide coding standards, enhancing readability and collaboration.
- Linters automate style guide enforcement, catching errors and improving code maintainability.

### Reduce complexity of method:
- Reduce method complexity by breaking it into smaller functions, avoiding nested loops, simplifying conditions, and use clear variable/method names.


# 7. Object-Oriented Programming (OOP)

### Class vs. Instance:
- **Class**: A blueprint for objects.
- **Instance**: An object created from a class blueprint.
- **Constructors**: Special methods to initialize new objects.

### Inheritance in OOP:
- Used when there's a clear "is-a" relationship, e.g., "Car is a Vehicle".

### Encapsulation in OOP:
- Hiding data within a class, accessed only through defined methods.
- A class that represents a "Car" with private attributes like "engine" and "fuel" only accessible through getter and setter methods, ensuring controlled access and modification.

### Interfaces vs. Abstract Classes:
- **Interfaces**: A contract that any class implementing it must adhere to. All of its methods are abstract (i.e., they have no body), and a class can implement multiple interfaces, ensuring flexibility and specificity in function definitions.
- **Abstract Classes**: A blueprint for other classes that allows for shared method implementations. It may contain both fully implemented methods and abstract methods (methods without a body). A class can inherit from only one abstract class.

# 8. Development Operations

### Merge Conflicts:
- Occur when changes in different branches overlap. Resolved manually.
- Je tam =HEAD=  a =origin/master=

### Version Control Workflow:
- Collaborators create branches, make commits, then merge them into the main branch.
- Pro každou funkci nová branch.

### Releasing Code to Production:
- Code is moved from development to staging/testing, then to production.
- 1. Připojit se na produkční server.
- 2. Pullnout verzi z gitu.
- 3. Zbuildit aplikaci na server.
- 4. Spustit aplikacei např. pres systemd

### Application Configuration:
- Ukázat application.properties, něco lokálně, něco pro server, enviroment variables.

### Able to build the app from the command line interface
- buildnu to přes command ./gradlew build a najdu to v build/libs
- .jar file najdu v libs, a to můžu but spustit pres java -jar mojeaplikace.jar a nebo deploynu mojeaplikace.jar na server

# 9. Error Handling

### Stack Trace:
- Shows the call stack when an exception occurs. Look for line numbers, method names, and file names.

### Runtime vs. Compile-time Errors:
- **Compile-time**: Detected by the compiler.
- **Runtime**: Occur during program execution.

### Error Handling in Java Spring:
- In Java Spring, errors can be managed using try-catch blocks and by throwing specific exceptions.

### Where and why to use data/input validation:
- At all entry points (e.g., form inputs, API endpoints). To prevent invalid data and potential security vulnerabilities.
- Vždycky na backendu validuju data, na frontendu to je v poho,

### Debugging Process:
1. Identify the Issue.
2. Isolate the Source.
3. Inspect Variables and Flow.
4. Formulate a Hypothesis.
5. Test the Hypothesis.
6. Fix and Verify.
7. Reflect and Learn.

