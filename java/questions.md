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


