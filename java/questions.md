# List of Questions #
- Performance Improvements
- Database Changes
- Server Migrations and Interfaces
- Relational and Non-Relational Databases
- HTTP Methods and REST APIs
- Promises and Asynchronous Programming
- Cultural Questions
- What is `System.out.println()` and how does it work?
- Are we able to extent arraylist how?
- Memory Leaks and Garbage Collection in Java
- How can you detect and fix memory leaks in Java?
## SDLC (Software Development Life Cycle)
- **Q:** How would you approach SDLC for developing a two-page application?  
## Non-Functional Requirements
- **Q:** What are non-functional requirements, and how should they be applied?  
## Java 8 Features
- **Q:** What new features were introduced in Java 8?  
## REST API Security
- **Q:** How do you secure REST APIs?  
## Integration Testing vs. System Testing
- **Q:** What is the difference between integration testing and system testing? 
## 1. Code for Deadlock Execution (One Thread Uses Same Resource)
### Deadlock Example Code:
### 2. Deadlock Example Using `Runnable`
- 3. Code for Writing Every 4th Character from a String
- 4. Code for Writing the 4th Character from Every Second Word

## Thread
- implemention of "completable feature" in Java

## Authentication

Authentication security validation

# Q&A on Various Topics in Java, Spring Boot, React, and DevOps

## Performance Improvements
**Q:** How would you improve the performance of a Spring Boot application?  
**A:** 
1. **Caching:** Use caching mechanisms like Redis to store frequently accessed data.
2. **Database Tuning:** Optimize database queries, indexes, and schema. Use pagination for large data sets.
3. **Connection Pooling:** Implement connection pooling for efficient database connections.
4. **Lazy Loading:** Use lazy initialization to avoid loading unnecessary data.
5. **Asynchronous Operations:** Offload long-running tasks using `@Async` in Spring.
6. **Batch Processing:** Use Spring Batch for bulk operations.
7. **Profiling:** Use tools like JProfiler or VisualVM to identify bottlenecks.

---

## Database Changes
**Q:** How would you handle database schema changes in a production environment?  
**A:** 
1. **Use Version Control for Database:** Tools like Flyway or Liquibase can manage schema migrations.
2. **Backward Compatibility:** Ensure changes are backward-compatible to avoid breaking existing functionality.
3. **Staging Environment:** Test changes in a staging environment before production.
4. **Data Backup:** Always back up the database before applying changes.
5. **Apply in Phases:** Deploy changes incrementally to reduce risk.
6. **Zero Downtime Deployments:** Consider techniques like rolling updates or blue-green deployments.

---

## Server Migrations and Interfaces
**Q:** How would you handle server migration and interfaces during a migration from TLS to MTLS?  
**A:** 
1. **Dual Support:** Implement dual support for TLS and MTLS, allowing a transition period where both are accepted.
2. **Configuration Management:** Update configurations for servers and clients to support MTLS (mutual TLS).
3. **Certificate Management:** Ensure proper certificate management (issuing, renewing, and revoking certificates).
4. **Testing:** Perform extensive testing in a staging environment, especially to verify secure connections.
5. **Load Balancer:** Update load balancers to route traffic based on MTLS requirements.

---

## Relational and Non-Relational Databases
**Q:** How do relational databases differ from non-relational databases?  
**A:** 
- **Relational Databases:** Use structured data with predefined schemas (e.g., SQL databases like MySQL, PostgreSQL). They ensure ACID compliance (Atomicity, Consistency, Isolation, Durability).
- **Non-Relational Databases:** Handle unstructured or semi-structured data (e.g., NoSQL databases like MongoDB, Cassandra). They are typically more flexible and scalable, designed for large-scale data that doesn't fit well in tables.

---

## HTTP Methods and REST APIs
**Q:** What HTTP methods are used in REST APIs and what are their purposes?  
**A:**
1. **GET:** Retrieve data from the server.
2. **POST:** Send data to the server to create a new resource.
3. **PUT:** Update an existing resource.
4. **PATCH:** Partially update an existing resource.
5. **DELETE:** Delete a resource on the server.

---

## Promises and Asynchronous Programming
**Q:** What is a callback in asynchronous programming?  
**A:** 
- A callback is a function passed as an argument to another function, which is then executed after the completion of the first function. In asynchronous programming, callbacks are used to handle tasks like HTTP requests, timers, or file I/O, where the execution of code doesn't stop to wait for the response.

---

## Cultural Questions
**Q:** What is your un-ideal work environment?  
**A:** An un-ideal work environment for me would be one that lacks collaboration, transparency, and growth opportunities. A place where communication is unclear, and there is little to no feedback, as it hinders personal development and teamwork.

---

## Java Specific Questions
**Q:** What is `System.out.println()` and how does it work?  
**A:** 
- `System` is a class in the `java.lang` package. `out` is a static field within the `System` class of type `PrintStream`, and `println()` is a method of the `PrintStream` class. When you call `System.out.println()`, it prints the argument passed to it and appends a newline.
- Here are some of the key features of the System class:

  - Fields:

- public static final InputStream in: The standard input stream, typically corresponding to keyboard input.
- public static final PrintStream out: The standard output stream, typically corresponding to console output.
- public static final PrintStream err: The standard error stream, typically corresponding to console error output.

  - Methods:

- arraycopy(Object src, int srcPos, Object dest, int destPos, int length): Copies an array of objects from one location to another.
- currentTimeMillis(): Returns the current time in milliseconds since January 1, 1970, 00:00:00 GMT.
- nanoTime(): Returns the current time in nanoseconds.
- exit(int status): Terminates the current Java VM with the specified exit status.
- getProperty(String key): Retrieves the value of a system property.
- getProperties(): Returns a Properties object containing all system properties.
- loadLibrary(String libname): Loads a native library.
- getenv(String name): Retrieves the value of an environment variable.
- gc(): Suggests that the garbage collector should run.
- The System class is essential for many common tasks in Java programming, such as reading input, writing output, working with system properties, and interacting with the operating system.

**Q:** Are we able to extent arraylist how?

**A:** Yes, you can extend the ArrayList class in Java. However, you cannot directly modify the existing ArrayList class, as it is a final class. Instead, you can create a new class that inherits from ArrayList and adds your own custom methods or fields.

- Here's a basic example of extending ArrayList to create a new class called MyArrayList:
```
import java.util.ArrayList;

public class MyArrayList extends ArrayList<String> {
    // Custom methods and fields can be added here
    public void printAllElements() {
        for (String element : this) {
            System.out.println(element);
        }
    }
}
```
In this example, MyArrayList inherits all the methods and fields from ArrayList. It also adds a new custom method called printAllElements() that prints all the elements in the list.

You can then create an instance of MyArrayList and use it like any other ArrayList:
```
MyArrayList list = new MyArrayList();
list.add("Hello");
list.add("world");
list.printAllElements();
```
This will output:
```
Hello
world
```
By extending ArrayList, you can create more specialized list implementations that meet your specific needs.

---

## Memory Leaks and Garbage Collection in Java
**Q:** How can you detect and fix memory leaks in Java?  
**A:**
- **Detection:** Use profiling tools like VisualVM, JProfiler, or Eclipse MAT to identify objects that are not being garbage collected.
- **Fixing:** 
  - Ensure all resources like database connections or streams are closed after use.
  - Avoid static references that may prevent objects from being garbage collected.
  - Be cautious with listeners or observers that aren’t properly deregistered.
  
**Q:** How does garbage collection work in Java?  
**A:** 
- Java's garbage collector automatically reclaims memory by removing objects that are no longer reachable from any active part of the program. It uses algorithms like Mark-and-Sweep and Generational Garbage Collection.

---

## SDLC (Software Development Life Cycle)
**Q:** How would you approach SDLC for developing a two-page application?  
**A:** 
1. **Requirement Gathering:** Understand the scope, objectives, and features.
2. **Design:** Draft UI wireframes, choose the tech stack (e.g., React for frontend, Spring Boot for backend).
3. **Implementation:** Write code for frontend components and backend APIs.
4. **Testing:** Conduct unit, integration, and user acceptance testing.
5. **Deployment:** Deploy using CI/CD pipelines to a production environment.
6. **Maintenance:** Monitor and fix bugs, optimize performance.

---

## Non-Functional Requirements
**Q:** What are non-functional requirements, and how should they be applied?  
**A:**
- Non-functional requirements define system attributes like performance, scalability, security, and usability. They should be considered at the design stage, ensuring the application is robust, performs well under load, is secure against threats, and meets usability standards.

---

## Java 8 Features
**Q:** What new features were introduced in Java 8?  
**A:**
1. **Lambda Expressions:** Provide a clear and concise way to represent a single method interface using an expression.
2. **Streams API:** Allows for functional-style operations on streams of elements.
3. **Optional:** Helps in avoiding null pointer exceptions by representing optional values.
4. **Default Methods in Interfaces:** Allow interfaces to have methods with implementation.

---

## REST API Security
**Q:** How do you secure REST APIs?  
**A:**
1. **Authentication & Authorization:** Use OAuth2, JWT (JSON Web Token) for secure authentication.
2. **HTTPS:** Ensure all communication happens over HTTPS to prevent man-in-the-middle attacks.
3. **Rate Limiting:** Implement rate limiting to prevent abuse of APIs.
4. **Input Validation:** Sanitize and validate all inputs to protect against injection attacks.
5. **CORS:** Configure Cross-Origin Resource Sharing to control access from different domains.

---

## Integration Testing vs. System Testing
**Q:** What is the difference between integration testing and system testing?  
**A:** 
- **Integration Testing:** Focuses on verifying the interactions between different modules or components.
- **System Testing:** Tests the entire system as a whole, ensuring all components work together as expected.

## 1. Code for Deadlock Execution (One Thread Uses Same Resource)
### Deadlock Example Code:
```java
public class DeadlockExample {

    public static void main(String[] args) {
        // Resources shared between threads
        final Object resource1 = new Object();
        final Object resource2 = new Object();

        // Thread 1 tries to lock resource1 and then resource2
        Thread thread1 = new Thread(() -> {
            synchronized (resource1) {
                System.out.println("Thread 1: Locked resource 1");

                // Simulate some work with resource1
                try { Thread.sleep(100); } catch (InterruptedException e) {}

                System.out.println("Thread 1: Waiting for resource 2");

                synchronized (resource2) {
                    System.out.println("Thread 1: Locked resource 2");
                }
            }
        });

        // Thread 2 tries to lock resource2 and then resource1
        Thread thread2 = new Thread(() -> {
            synchronized (resource2) {
                System.out.println("Thread 2: Locked resource 2");

                // Simulate some work with resource2
                try { Thread.sleep(100); } catch (InterruptedException e) {}

                System.out.println("Thread 2: Waiting for resource 1");

                synchronized (resource1) {
                    System.out.println("Thread 2: Locked resource 1");
                }
            }
        });

        // Start both threads
        thread1.start();
        thread2.start();
    }
}
```

---

## 2. Deadlock Example Using `Runnable`

```java
public class DeadlockRunnableExample {

    public static void main(String[] args) {
        // Shared resources between threads
        final Object resource1 = new Object();
        final Object resource2 = new Object();

        // Runnable task for Thread 1: locks resource1 and then tries to lock resource2
        Runnable task1 = () -> {
            synchronized (resource1) {
                System.out.println("Thread 1: Locked resource 1");

                // Simulate some work with resource1
                try { Thread.sleep(100); } catch (InterruptedException e) { }

                System.out.println("Thread 1: Waiting for resource 2");

                synchronized (resource2) {
                    System.out.println("Thread 1: Locked resource 2");
                }
            }
        };

        // Runnable task for Thread 2: locks resource2 and then tries to lock resource1
        Runnable task2 = () -> {
            synchronized (resource2) {
                System.out.println("Thread 2: Locked resource 2");

                // Simulate some work with resource2
                try { Thread.sleep(100); } catch (InterruptedException e) { }

                System.out.println("Thread 2: Waiting for resource 1");

                synchronized (resource1) {
                    System.out.println("Thread 2: Locked resource 1");
                }
            }
        };

        // Create and start threads with the Runnable tasks
        Thread thread1 = new Thread(task1);
        Thread thread2 = new Thread(task2);

        // Start both threads
        thread1.start();
        thread2.start();
    }
}
```

---

## 3. Code for Writing Every 4th Character from a String

```java
public class EveryFourthCharacter {

    public static void main(String[] args) {
        // Input string
        String input = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        
        // Output every 4th character
        System.out.println("Every 4th character:");
        for (int i = 3; i < input.length(); i += 4) {  // Start at index 3 for the 4th character
            System.out.print(input.charAt(i) + " ");
        }
    }
}
```

**Sample Output:**
```
Every 4th character:
D H L P T X
```

---

## 4. Code for Writing the 4th Character from Every Second Word

```java
public class EverySecondWordFourthCharacter {

    public static void main(String[] args) {
        // Input string
        String input = "This is an example string to demonstrate the extraction of every second word's fourth character.";
        
        // Split the input string into words
        String[] words = input.split(" ");
        
        // Iterate through every second word and extract the 4th character (if it exists)
        System.out.println("4th character of every second word:");
        for (int i = 1; i < words.length; i += 2) {  // Start from the second word (index 1)
            if (words[i].length() >= 4) {  // Check if the word has at least 4 characters
                System.out.print(words[i].charAt(3) + " ");  // Print the 4th character (index 3)
            }
        }
    }
}
```

**Sample Output:**
```
4th character of every second word:
m t t c
```

## Thread

### implemention of "completable feature" in Java

To implement a "completable feature" in Java, you would typically use CompletableFuture, which is part of the java.util.concurrent package introduced in Java 8. It provides an easy way to handle asynchronous computations without manually dealing with threads.

- Example: Using CompletableFuture
Let’s assume you are building a feature where you need to make multiple independent API calls asynchronously, process their results, and then combine them when all tasks are complete.

- Key Concepts:
  - Run Asynchronously: Start a task in the background without blocking the main thread.
  - Combine Results: Combine results of multiple asynchronous operations.
  - Handle Exceptions: Handle exceptions in asynchronous computations.

- Basic CompletableFuture Example
```
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureExample {

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        
        // Example of a simple async computation
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            // Simulate long-running task (e.g., API call)
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                throw new IllegalStateException(e);
            }
            return "Result of the asynchronous computation";
        });
        
        // Non-blocking call, you can continue doing other work
        System.out.println("Doing other work while the future completes...");
        
        // Block and wait for the result
        String result = future.get();  // This blocks until the future is complete
        
        System.out.println("Completed future result: " + result);
    }
}
```

- CompletableFuture with Chaining
  You can chain multiple asynchronous tasks together using methods like thenApply(), thenCompose(), and thenCombine().

  - thenApply: Transforms the result of a CompletableFuture.
  - thenCombine: Combines the result of two CompletableFutures.

```
import java.util.concurrent.CompletableFuture;

public class CompletableFeatureChaining {

    public static void main(String[] args) throws Exception {

        CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> {
            // Simulate a time-consuming task
            System.out.println("Task 1 - Fetching number");
            return 5;
        });

        CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> {
            System.out.println("Task 2 - Fetching number");
            return 10;
        });

        // Combine the results of both futures
        CompletableFuture<Integer> combinedFuture = future1.thenCombine(future2, (num1, num2) -> {
            System.out.println("Task 3 - Combining results");
            return num1 + num2;
        });

        // Wait for the combined result
        System.out.println("Combined result: " + combinedFuture.get());
    }
}
```

- Exception Handling: You can handle exceptions in CompletableFuture using methods like exceptionally() or handle().
```
import java.util.concurrent.CompletableFuture;

public class CompletableFutureExceptionHandling {

    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            // Simulate an exception
            if (true) {
                throw new RuntimeException("Something went wrong!");
            }
            return "Success!";
        }).exceptionally(ex -> {
            System.out.println("Exception occurred: " + ex.getMessage());
            return "Recovered from failure";
        });

        // Print the result
        System.out.println(future.join());  // Blocks and returns the result
    }
}
```

- Combining Multiple CompletableFutures: If you have multiple CompletableFutures and you want to wait for all of them to complete, you can use CompletableFuture.allOf():

```
import java.util.concurrent.CompletableFuture;

public class CompletableFutureAllOf {

    public static void main(String[] args) throws Exception {

        CompletableFuture<Void> future1 = CompletableFuture.runAsync(() -> {
            System.out.println("Task 1 is running");
        });

        CompletableFuture<Void> future2 = CompletableFuture.runAsync(() -> {
            System.out.println("Task 2 is running");
        });

        CompletableFuture<Void> future3 = CompletableFuture.runAsync(() -> {
            System.out.println("Task 3 is running");
        });

        // Wait for all futures to complete
        CompletableFuture<Void> allFutures = CompletableFuture.allOf(future1, future2, future3);

        // Block until all tasks are done
        allFutures.join();
        System.out.println("All tasks are completed!");
    }
}

```

- Advanced Use Case: HTTP Requests with CompletableFuture: Imagine you need to make two API calls and combine their results.

```
import java.util.concurrent.CompletableFuture;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.net.URI;

public class CompletableFutureWithHttp {

    public static void main(String[] args) throws Exception {

        HttpClient client = HttpClient.newHttpClient();

        CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> {
            try {
                HttpRequest request = HttpRequest.newBuilder()
                        .uri(new URI("https://jsonplaceholder.typicode.com/posts/1"))
                        .build();
                HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
                return response.body();
            } catch (Exception e) {
                throw new RuntimeException(e);
            }
        });

        CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> {
            try {
                HttpRequest request = HttpRequest.newBuilder()
                        .uri(new URI("https://jsonplaceholder.typicode.com/posts/2"))
                        .build();
                HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
                return response.body();
            } catch (Exception e) {
                throw new RuntimeException(e);
            }
        });

        // Combine the results of both API calls
        CompletableFuture<String> combinedFuture = future1.thenCombine(future2, (response1, response2) -> {
            return "Combined Result: \n" + response1 + "\n" + response2;
        });

        // Block and get the final result
        System.out.println(combinedFuture.get());
    }
}
```

### Conclusion: Key Methods in CompletableFuture

- supplyAsync(): Runs a task asynchronously and returns a result.
- thenApply(): Transforms the result of a CompletableFuture.
- thenCombine(): Combines the results of two CompletableFutures.
- exceptionally(): Handles exceptions.
- allOf(): Waits for all the CompletableFutures to complete

## Auth Security Validation in Java and Spring Boot

### 1. **What is Authentication and Authorization?**
- **Authentication**: The process of verifying the identity of a user, often by checking credentials like a username and password.
- **Authorization**: Determines what actions an authenticated user is allowed to perform within the system.

### 2. **What are some common authentication mechanisms?**
- **Basic Authentication**: Involves sending the username and password encoded in Base64 over HTTP headers. It's simple but not secure unless used over HTTPS.
- **OAuth2**: An open standard for token-based authentication and authorization. OAuth2 is widely used in REST APIs and mobile applications.
- **JWT (JSON Web Tokens)**: A compact, self-contained way to securely transmit information between parties as a JSON object. It's commonly used for authorization in modern web applications.

### 3. **How does Spring Security handle Authentication and Authorization?**
Spring Security is a powerful framework for securing Spring-based applications. It provides support for multiple authentication mechanisms.

- **Authentication**: Spring Security provides `AuthenticationManager` and `AuthenticationProvider` interfaces to handle different types of authentication mechanisms. Credentials are validated against the configured data source (e.g., in-memory, database, LDAP).
  
- **Authorization**: Once authenticated, Spring Security applies access control rules based on roles and authorities. This is managed through the `@PreAuthorize`, `@Secured`, or through configuration using the `HttpSecurity` object.

### 4. **How can you secure REST APIs?**
To secure REST APIs in Spring Boot:
- Use **OAuth2** or **JWT** for stateless authentication.
- Implement **CORS (Cross-Origin Resource Sharing)** policies to control which domains can access your APIs.
- Apply **rate limiting** to prevent abuse and Distributed Denial-of-Service (DDoS) attacks.
- Use **HTTPS** to encrypt data in transit.
  
#### Example of JWT Security in Spring Boot:
```java
// SecurityConfig.java
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .csrf().disable()
            .authorizeRequests()
            .antMatchers("/api/auth/**").permitAll()
            .anyRequest().authenticated()
            .and()
            .addFilter(new JwtAuthenticationFilter(authenticationManager()))
            .addFilter(new JwtAuthorizationFilter(authenticationManager()));
    }
}
```
### 5. What methods can be used to validate JWT Tokens?
- Signature Verification: JWT tokens are signed using a secret key. Validate the signature to ensure the token is untampered.
- Token Expiry: Check the token's expiration (exp) claim to ensure it is still valid.
- Custom Claims: Verify custom claims within the token to meet application-specific requirements (e.g., roles, scopes).

### 6. How to handle Password Encryption?
Never store passwords in plain text. Use encryption techniques such as:

- BCrypt: A password hashing function that includes a salt to guard against rainbow table attacks.
Example of Using BCrypt in Spring Boot:
```java
@Bean
public PasswordEncoder passwordEncoder() {
    return new BCryptPasswordEncoder();
}
```

### 7. How to Protect Against Common Security Threats?
- SQL Injection: Use prepared statements to avoid malicious SQL queries.
- Cross-Site Scripting (XSS): Sanitize inputs and use output encoding to prevent XSS attacks.
- Cross-Site Request Forgery (CSRF): Enable CSRF protection in forms and validate the CSRF token.
- Session Hijacking: Use HttpOnly and Secure flags for cookies and apply session timeout policies.

## Core Java Concepts
1. **Explain the Java Memory Model. What are the differences between stack and heap memory?**
  - The Java Memory Model defines how threads interact through memory and what behaviors are allowed in concurrent execution.
  - **Stack Memory:** Used for static memory allocation, stores primitive data types and object references, follows LIFO (Last In First Out) order.
  - **Heap Memory:** Used for dynamic memory allocation, stores objects and their instance variables, and is managed by the garbage collector.

2. **What are the differences between `HashMap` and `ConcurrentHashMap`? When would you choose one over the other?**
  - `HashMap` is not thread-safe, and multiple threads can cause data corruption if accessed concurrently. `ConcurrentHashMap` is thread-safe and allows concurrent read and write operations.
  - Choose `HashMap` for single-threaded applications for better performance; choose `ConcurrentHashMap` for multi-threaded applications needing safe concurrent access.

3. **Describe the Java Stream API. How does it differ from traditional collections processing?**
  - The Java Stream API allows functional-style operations on streams of elements, enabling operations like map, filter, and reduce.
  - It differs from traditional collections processing by enabling operations on collections in a more declarative and concise manner and providing lazy evaluation, which improves performance.

4. **What is the difference between `==` and `equals()` in Java? How would you override `equals()` and `hashCode()`?**
  - `==` checks for reference equality (i.e., whether two references point to the same object), while `equals()` checks for value equality (i.e., whether two objects are logically equivalent).
  - To override `equals()`, compare the fields of the objects to determine if they are equal. When overriding `equals()`, you must also override `hashCode()` to maintain the contract between the two.

5. **Explain the concept of Java Generics. Why are they useful? Can you provide an example of a generic class?**
  - Java Generics enable types (classes and interfaces) to be parameters when defining classes, interfaces, and methods, allowing for code reusability and type safety.
  - Example of a generic class:
    ```java
    public class Box<T> {
        private T item;
        public void setItem(T item) { this.item = item; }
        public T getItem() { return item; }
    }
    ```

## Object-Oriented Programming (OOP)
1. **Can you explain the four principles of OOP? Provide examples of each in Java.**
  - **Encapsulation:** Bundling data (fields) and methods (functions) together in a class. Example: Using private fields with public getter/setter methods.
  - **Inheritance:** Mechanism where one class inherits the fields and methods of another. Example: `class Dog extends Animal {}`.
  - **Polymorphism:** Ability for different classes to be treated as instances of the same class through interfaces or inheritance. Example: method overriding.
  - **Abstraction:** Hiding complex implementation details and showing only essential features. Example: abstract classes and interfaces.

2. **What is polymorphism in Java? How does method overloading differ from method overriding?**
  - Polymorphism allows methods to do different things based on the object that it is acting upon.
  - **Method Overloading:** Same method name with different parameters within the same class.
  - **Method Overriding:** Same method name and parameters in a subclass that provides a specific implementation of a method defined in its superclass.

3. **How do you achieve abstraction in Java? Provide an example using abstract classes and interfaces.**
  - Abstraction in Java is achieved through abstract classes and interfaces.
  - Example of an abstract class:
    ```java
    abstract class Animal {
        abstract void sound(); // abstract method
    }
    class Dog extends Animal {
        void sound() { System.out.println("Bark"); }
    }
    ```

## Concurrency and Multithreading
1. **How do you create a thread in Java? Discuss the differences between extending `Thread` and implementing `Runnable`.**
  - A thread can be created by extending the `Thread` class or implementing the `Runnable` interface.
  - **Extending `Thread`:** The class inherits from `Thread`, and you override the `run()` method. Example:
    ```java
    class MyThread extends Thread {
        public void run() { System.out.println("Thread running"); }
    }
    ```
  - **Implementing `Runnable`:** Implement the `Runnable` interface and provide the `run()` method. Example:
    ```java
    class MyRunnable implements Runnable {
        public void run() { System.out.println("Runnable running"); }
    }
    ```
  - Using `Runnable` is preferred for better design as it allows for separation of concerns and can be used with multiple threads.

2. **What are `synchronized` methods and blocks? How do they differ from `ReentrantLock`?**
  - **Synchronized methods/blocks:** Ensures that only one thread can access the method/block at a time, preventing concurrent access.
  - **ReentrantLock:** An implementation of the Lock interface that provides more advanced locking capabilities than synchronized methods. It allows for timed locking, interruptible locks, and can be locked by the same thread multiple times.
  - ReentrantLock provides more flexibility and features, while synchronized is simpler to use.

3. **Explain the producer-consumer problem. How would you implement it in Java using `BlockingQueue`?**
  - The producer-consumer problem is a classic concurrency issue where one or more producers generate data and one or more consumers use that data.
  - Implementation using `BlockingQueue`:
    ```java
    BlockingQueue<Integer> queue = new ArrayBlockingQueue<>(10);
    // Producer
    new Thread(() -> {
        while (true) {
            try {
                queue.put(item); // Add item to queue
            } catch (InterruptedException e) { Thread.currentThread().interrupt(); }
        }
    }).start();
    // Consumer
    new Thread(() -> {
        while (true) {
            try {
                Integer item = queue.take(); // Retrieve item from queue
            } catch (InterruptedException e) { Thread.currentThread().interrupt(); }
        }
    }).start();
    ```

4. **What is the Java `CompletableFuture`? How does it improve upon traditional approaches to asynchronous programming?**
  - `CompletableFuture` is a class that represents a future result of an asynchronous computation. It allows for non-blocking operations and can be combined with other futures.
  - It improves upon traditional approaches by providing a fluent API for combining multiple asynchronous computations, handling exceptions, and making code more readable and maintainable.

## Design Patterns
1. **Explain the Singleton Design Pattern. How would you implement it in a thread-safe manner?**
  - The Singleton Design Pattern ensures that a class has only one instance and provides a global point of access to it.
  - A thread-safe implementation can be done using double-checked locking:
    ```java
    public class Singleton {
        private static volatile Singleton instance;
        private Singleton() {}
        public static Singleton getInstance() {
            if (instance == null) {
                synchronized (Singleton.class) {
                    if (instance == null) {
                        instance = new Singleton();
                    }
                }
            }
            return instance;
        }
    }
    ```

2. **What is the Factory Design Pattern? Provide a scenario where you would use it.**
  - The Factory Design Pattern defines an interface for creating objects but lets subclasses decide which class to instantiate.
  - It is useful in scenarios where the exact type of object to create is determined at runtime, such as creating different types of payment processors based on user selection (e.g., credit card, PayPal).

3. **Can you explain the Observer Design Pattern? How would you implement it in Java?**
  - The Observer Design Pattern defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
  - Implementation example:
    ```java
    interface Observer {
        void update(String message);
    }
    class Subject {
        private List<Observer> observers = new ArrayList<>();
        public void addObserver(Observer observer) { observers.add(observer); }
        public void notifyObservers(String message) {
            for (Observer observer : observers) {
                observer.update(message);
            }
        }
    }
    ```

## Spring Framework (if applicable)
1. **What are the differences between Spring and Spring Boot?**
  - Spring is a comprehensive framework for enterprise Java applications, while Spring Boot is a subproject that simplifies the setup and development of new Spring applications by providing out-of-the-box configurations and embedded servers.

2. **Explain Dependency Injection in Spring. How does it improve code quality?**
  - Dependency Injection is a design pattern that allows the creation of dependent objects outside of a class and provides those objects to a class in various ways (constructor injection, setter injection).
  - It improves code quality by promoting loose coupling, making the code easier to test, maintain, and extend.

3. **What is the purpose of the `@Transactional` annotation? How does it work?**
  - The `@Transactional` annotation is used to define the scope of a transaction in Spring, ensuring that multiple operations are performed within a single transaction context.
  - When a method annotated with `@Transactional` is executed, Spring manages the transaction, rolling back if any

### Coding Challenges
1. **Reverse a String in Java**
```java
```
2. Write a Java function to check if a string is a palindrome.
   A palindrome is a string that reads the same forward and backward.
```java
public class PalindromeChecker {
    public static boolean isPalindrome(String str) {
        int left = 0;
        int right = str.length() - 1;
        
        while (left < right) {
            if (str.charAt(left) != str.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }

    public static void main(String[] args) {
        System.out.println(isPalindrome("racecar")); // true
        System.out.println(isPalindrome("hello"));   // false
    }
}
```
2. Implement a method to find the longest substring without repeating characters.
   This problem can be solved using a sliding window approach. 
```java
import java.util.HashSet;
import java.util.Set;

public class LongestSubstring {
    public static int lengthOfLongestSubstring(String s) {
        int n = s.length();
        int maxLength = 0;
        int left = 0;
        Set<Character> set = new HashSet<>();

        for (int right = 0; right < n; right++) {
            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left));
                left++;
            }
            set.add(s.charAt(right));
            maxLength = Math.max(maxLength, right - left + 1);
        }
        return maxLength;
    }

    public static void main(String[] args) {
        System.out.println(lengthOfLongestSubstring("abcabcbb")); // 3
        System.out.println(lengthOfLongestSubstring("bbbbb"));    // 1
    }
}
```
3. Write a program to merge two sorted arrays into a single sorted array.
      This can be done using a two-pointer technique.
```java
import java.util.Arrays;

public class MergeSortedArrays {
    public static int[] merge(int[] arr1, int[] arr2) {
        int n1 = arr1.length;
        int n2 = arr2.length;
        int[] mergedArray = new int[n1 + n2];
        int i = 0, j = 0, k = 0;

        while (i < n1 && j < n2) {
            if (arr1[i] <= arr2[j]) {
                mergedArray[k++] = arr1[i++];
            } else {
                mergedArray[k++] = arr2[j++];
            }
        }

        while (i < n1) {
            mergedArray[k++] = arr1[i++];
        }

        while (j < n2) {
            mergedArray[k++] = arr2[j++];
        }

        return mergedArray;
    }

    public static void main(String[] args) {
        int[] arr1 = {1, 3, 5, 7};
        int[] arr2 = {2, 4, 6, 8};
        System.out.println(Arrays.toString(merge(arr1, arr2))); // [1, 2, 3, 4, 5, 6, 7, 8]
    }
}
```
5. Implement a function to perform depth-first search (DFS) on a binary tree.
   DFS can be implemented using recursion.
```java
class TreeNode {
    int val;
    TreeNode left, right;

    TreeNode(int val) {
        this.val = val;
        left = right = null;
    }
}

public class DepthFirstSearch {
    public static void dfs(TreeNode node) {
        if (node == null) {
            return;
        }
        System.out.print(node.val + " ");
        dfs(node.left);
        dfs(node.right);
    }

    public static void main(String[] args) {
        TreeNode root = new TreeNode(1);
        root.left = new TreeNode(2);
        root.right = new TreeNode(3);
        root.left.left = new TreeNode(4);
        root.left.right = new TreeNode(5);

        dfs(root); // Output: 1 2 4 5 3
    }
}
```
### Flat map
### 2 sort array, mearge into one with minimum complexcity.
### click on points and give undo it (React)
### auto suggestion react
### Rolling balls algoritham

