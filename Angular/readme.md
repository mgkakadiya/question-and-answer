# Q-A

# Atomic Design in Front-End Development
# What is atomic design in FE, dumb and smart components?
## Atomic Design

**Atomic Design** is a methodology for creating design systems, introduced by Brad Frost. It is based on the concept of breaking down a user interface into its smallest parts and building them up into increasingly complex structures. The methodology comprises five stages:

1. **Atoms**: These are the most basic building blocks of the design. Examples include buttons, input fields, labels, and icons.
2. **Molecules**: These are simple groups of atoms functioning together as a unit. For example, a form label, input field, and button can combine to form a search form molecule.
3. **Organisms**: These are relatively complex components composed of groups of molecules and/or atoms. For instance, a header section that includes a logo, navigation, and search form.
4. **Templates**: These are page-level objects that place components into a layout and articulate the design’s underlying content structure.
5. **Pages**: These are specific instances of templates. They combine real content with the template to form a view that is representative of the final interface.

## Dumb and Smart Components

**Dumb (Presentational) Components** and **Smart (Container) Components** are terms often used in React development to distinguish between two types of components based on their responsibilities.

### Dumb (Presentational) Components

- **Purpose**: Focus on how things look.
- **Characteristics**:
  - Receive data and callbacks exclusively via props.
  - Do not manage their own state (other than UI state, like form inputs).
  - Contain little to no logic beyond UI logic.
  - Are reusable across different parts of the application.
  - Typically written as functional components.
  
- **Example**:
  ```jsx
  const Button = ({ label, onClick }) => (
    <button onClick={onClick}>{label}</button>
  );


- ### Smart (Container) Components
- **Purpose**: Focus on how things work.
- **Characteristics**:
  - Provide data and behavior to presentational (dumb) components.
  - Manage their own state and lifecycle methods.
  - Handle fetching data, updating state, and other logic-heavy tasks.
  - Typically written as class components or functional components using hooks.
- **Example**:
  ```jsx
  class ButtonContainer extends React.Component {
  state = { label: "Click Me" };

  handleClick = () => {
    this.setState({ label: "Clicked" });
  };

  render() {
    return (
      <Button
        label={this.state.label}
        onClick={this.handleClick}
      />
    );
  }
  }

- ### Summary
- **Atomic Design** is a methodology for structuring design systems, starting from the smallest elements (atoms) and building up to full pages.
- **Dumb** and **Smart Components** differentiate between UI-focused components that are purely presentational and logic-focused components that manage data and state.
By using these concepts, developers can create more maintainable, scalable, and consistent front-end architectures.



### `angular.json` File

The `angular.json` file is a crucial configuration file for Angular projects, defining how the Angular CLI should build and serve your application. This file contains settings for various aspects of your Angular project, such as the build options, development server configurations, and test configurations. Here’s an overview of its key sections:

## Overview of `angular.json`

- **version**: Specifies the version of the Angular CLI that this configuration is compatible with.

- **newProjectRoot**: Defines the directory where new projects will be created.

- **projects**: Lists all projects in the workspace. Each project can have its own set of configurations. A project can be an application or a library.

## Key Sections of a Project Configuration

- **projectType**: Specifies the type of the project, either `application` or `library`.

- **root**: The root directory for the project files.

- **sourceRoot**: The root directory for the source files of the project.

- **prefix**: A prefix that is applied to the selectors of components in this project to ensure they are unique.

- **architect**: Contains the build targets and their configurations. The most common targets are `build`, `serve`, `test`, `lint`, and `e2e`.

## Architect Targets

1. **build**: Configuration for building the project.
    - **builder**: The builder used for this target, typically `@angular-devkit/build-angular:browser`.
    - **options**: Default options for the build target, such as `outputPath`, `index`, `main`, `tsConfig`, `assets`, `styles`, and `scripts`.
    - **configurations**: Different configurations for the build, such as `production` or `development`. These can override the default options.

2. **serve**: Configuration for serving the project locally.
    - **builder**: The builder used for this target, typically `@angular-devkit/build-angular:dev-server`.
    - **options**: Default options for serving the application, such as `port` and `proxyConfig`.
    - **configurations**: Different configurations for serving, similar to the build target.

3. **test**: Configuration for running unit tests.
    - **builder**: The builder used for this target, typically `@angular-devkit/build-angular:karma`.
    - **options**: Options for running tests, such as `main`, `polyfills`, `tsConfig`, `karmaConfig`, `assets`, `styles`, and `scripts`.

4. **lint**: Configuration for linting the project.
    - **builder**: The builder used for this target, typically `@angular-devkit/build-angular:tslint`.
    - **options**: Options for linting, such as `tsConfig` and `exclude`.

5. **e2e**: Configuration for running end-to-end tests.
    - **builder**: The builder used for this target, typically `@angular-devkit/build-angular:protractor`.
    - **options**: Options for running e2e tests, such as `protractorConfig`.

## Example of `angular.json` Structure

Here is a simplified example of what an `angular.json` file might look like:

```json
{
  "version": 1,
  "newProjectRoot": "projects",
  "projects": {
    "my-app": {
      "projectType": "application",
      "root": "",
      "sourceRoot": "src",
      "prefix": "app",
      "architect": {
        "build": {
          "builder": "@angular-devkit/build-angular:browser",
          "options": {
            "outputPath": "dist/my-app",
            "index": "src/index.html",
            "main": "src/main.ts",
            "polyfills": "src/polyfills.ts",
            "tsConfig": "tsconfig.app.json",
            "assets": [
              "src/favicon.ico",
              "src/assets"
            ],
            "styles": [
              "src/styles.css"
            ],
            "scripts": []
          },
          "configurations": {
            "production": {
              "fileReplacements": [
                {
                  "replace": "src/environments/environment.ts",
                  "with": "src/environments/environment.prod.ts"
                }
              ],
              "optimization": true,
              "outputHashing": "all",
              "sourceMap": false,
              "extractCss": true,
              "namedChunks": false,
              "aot": true,
              "extractLicenses": true,
              "vendorChunk": false,
              "buildOptimizer": true
            }
          }
        },
        "serve": {
          "builder": "@angular-devkit/build-angular:dev-server",
          "options": {
            "browserTarget": "my-app:build"
          },
          "configurations": {
            "production": {
              "browserTarget": "my-app:build:production"
            }
          }
        },
        "test": {
          "builder": "@angular-devkit/build-angular:karma",
          "options": {
            "main": "src/test.ts",
            "polyfills": "src/polyfills.ts",
            "tsConfig": "tsconfig.spec.json",
            "karmaConfig": "karma.conf.js",
            "assets": [
              "src/favicon.ico",
              "src/assets"
            ],
            "styles": [
              "src/styles.css"
            ],
            "scripts": []
          }
        },
        "lint": {
          "builder": "@angular-devkit/build-angular:tslint",
          "options": {
            "tsConfig": [
              "tsconfig.app.json",
              "tsconfig.spec.json"
            ],
            "exclude": [
              "**/node_modules/**"
            ]
          }
        },
        "e2e": {
          "builder": "@angular-devkit/build-angular:protractor",
          "options": {
            "protractorConfig": "e2e/protractor.conf.js",
            "devServerTarget": "my-app:serve"
          },
          "configurations": {
            "production": {
              "devServerTarget": "my-app:serve:production"
            }
          }
        }
      }
    }
  },
  "defaultProject": "my-app"
}
```

## Summary
- angular.json is a configuration file for Angular projects, defining how the Angular CLI should build and serve your application.
- It includes settings for build options, development server configurations, test configurations, and more.
- The file is organized into sections for projects, each of which can have multiple targets (e.g., build, serve, test) with their own configurations.

Understanding and properly configuring the angular.json file is essential for effective Angular project management.



### What is Decorator in nest js?

# Decorators in NestJS

In NestJS, a **decorator** is a special kind of declaration that can be attached to classes, methods, properties, or parameters. Decorators add metadata to these entities, which NestJS can use to provide additional functionality, like routing, dependency injection, and more. Decorators are a fundamental part of NestJS and are heavily inspired by Angular's decorator system.

## Types of Decorators in NestJS

### 1. Class Decorators

Class decorators are used to define metadata for a class. They can configure how a class should be instantiated and used.

- **`@Controller`**: Marks a class as a NestJS controller, which can handle incoming requests and return responses.

  ```typescript
  import { Controller, Get } from '@nestjs/common';

  @Controller('cats')
  export class CatsController {
    @Get()
    findAll() {
      return 'This action returns all cats';
    }
  }

@Injectable: Marks a class as a provider that can be injected as a dependency.

### 2. Method Decorators
Method decorators are used to define metadata for class methods. They can specify how a method should handle incoming requests or manage the method's behavior.

@Get, @Post, @Put, @Delete, @Patch, @Options, @Head: These decorators define route handlers for HTTP methods.

### 3. Property Decorators
Property decorators are used to define metadata for class properties. They can configure how properties should be injected or managed.

@Inject: Injects a specific provider into a property.
@Autowired: Allows automatic dependency injection into properties (although this is less common and typically done via constructor injection).

### 4. Parameter Decorators
Parameter decorators are used to define metadata for parameters of class methods. They can extract specific information from the request and pass it as a parameter to the method.

@Param: Extracts a route parameter.
@Body: Extracts the body of a request.
@Query: Extracts query parameters.

### Summary
- Decorators in NestJS provide a powerful way to add metadata and configure the behavior of classes, methods, properties, and parameters. They enable a declarative approach to defining routes, dependency injection, guards, and more, making it easier to build scalable and maintainable applications.


# `forkJoin` in RxJS

In RxJS, `forkJoin` is an operator that allows you to execute multiple observables concurrently and wait for all of them to complete. It waits for all observables provided as arguments to emit at least one value and then emits an array of the last values from each observable.

## How `forkJoin` Works

- It takes multiple observables as arguments or an array of observables.
- It subscribes to each observable simultaneously.
- It collects the last emitted value from each observable.
- Once all observables complete (emit a complete notification), it emits an array containing the last emitted value from each observable.

## Example Usage

```typescript
import { forkJoin, of } from 'rxjs';

const observable1$ = of('Hello');
const observable2$ = of('World');

forkJoin({
  first: observable1$,
  second: observable2$
}).subscribe({
  next: ([result1, result2]) => {
    console.log(`Combined result: ${result1} ${result2}`);
  },
  complete: () => {
    console.log('All observables completed.');
  }
});
```

## In this example:

- `forkJoin` combines `observable1$` and `observable2$`.
- It waits for both observables to emit their values (`'Hello'` and `'World'` respectively).
- Once both observables emit a complete notification, it outputs `Combined result: Hello World`.

## Important Notes

- If any observable provided to `forkJoin` does not emit at least one value and complete, `forkJoin` will never emit and will hang indefinitely.
- `forkJoin` is often used in scenarios where you need to fetch data from multiple sources and wait for all responses before proceeding.
- This operator is particularly useful for scenarios such as making multiple HTTP requests and combining their results, or combining data from different parts of an application where the order of completion matters.

## Lifecycle Hooks

After your application instantiates a component or directive by calling its constructor, Angular calls the hook methods you have implemented at the appropriate point in the lifecycle of that instance.

- ngOnChanges
- ngOnInit
- ngDoCheck
- ngAfterContentInit
- ngAfterContentChecked
- ngAfterViewInit
- ngAfterViewChecked
- ngOnDestroy

## Async Pipe

The async pipe subscribes to an Observable or Promise and returns the latest value it has emitted. When a new value is emitted, the async pipe marks the component to be checked for changes. When the component gets destroyed, the async pipe unsubscribes automatically to avoid potential memory leaks. When the reference of the expression changes, the async pipe automatically unsubscribes from the old Observable or Promise and subscribes to the new one.

## Types of Pipes

Angular pipes let you declare display-value transformations in your template HTML. A class with the @Pipe decorator defines a function that transforms input values to output values for display in a view.

Angular defines various pipes, such as the date pipe and currency pipe.

- AsyncPipe
- CurrencyPipe
- DatePipe
- DecimalPipe
- I18nPluralPipe
- I18nSelectPipe
- JsonPipe
- KeyValuePipe
- LowerCasePipe
- PercentPipe
- SlicePipe
- TitleCasePipe
- UpperCasePipe

## What is ng-content and its purpose?

The ng-content is used to insert the content dynamically inside the component that helps to increase component reusability.

## What is Dependency Injection?

Dependency Injection (DI) is a design pattern used in software development, including in frameworks like Angular, to manage the dependencies between different components or services. It enables the creation, management, and injection of dependencies into classes or components, rather than having the classes or components create the dependencies themselves.

## Components and Directives Difference

### Components

- A component is a core concept in Angular and represents a self-contained, reusable UI element.
- A component consists of a template, which defines the structure and layout of the component, and a TypeScript class, which defines the component's behavior and data.
- Components have a view associated with them and are typically used to create UI elements such as forms, buttons, lists, etc.
- Components have a lifecycle with hooks.

### Directives

- Directives are instructions in the DOM that extend or modify the behavior of existing elements or components.
- Directives can be categorized into two types: structural and attribute directives.
- Structural directives modify the structure of the DOM by adding, removing, or manipulating elements. Examples include ngIf, ngFor, and ngSwitch.
- Attribute directives modify the behavior or appearance of an element. Examples include ngClass, ngStyle, and custom directives.
- Directives do not have their own templates or styles.
- Directives are typically used to add additional functionality, behavior, or styling to existing elements or components.
- Directives can also have their own lifecycle hooks, such as ngOnInit, ngOnChanges, ngOnDestroy, etc., similar to components.

## How to Unsubscribe in RxJS

### Observables in Angular

Angular makes use of observables as an interface to handle a variety of common asynchronous operations. For example:

- The HTTP module uses observables to handle AJAX requests and responses.
- The Router and Forms modules use observables to listen for and respond to user-input events.

### Unsubscribing using unsubscribe() method:

```typescript
import { Observable, interval, Subject } from 'rxjs';
import { takeUntil } from 'rxjs/operators';

const myObservable = interval(1000); // Emits values every second

const stopSignal = new Subject(); // Observable to signal when to stop

myObservable
  .pipe(takeUntil(stopSignal))
  .subscribe(value => console.log(value));

// Unsubscribe after some time
setTimeout(() => {
  stopSignal.next(); // Emit a value to stop the subscription
}, 5000);
```
# Differences Between Promise and Observable

## Promise
Promises deal with one asynchronous event at a time. They represent a single value that will be resolved or rejected in the future.

## Observable
Observables handle a sequence of asynchronous events over a period of time. They can emit multiple values asynchronously and are cancellable.

# JIT and AOT Compilation in Angular

## Ahead-of-Time (AOT)
AOT compiles your Angular application and libraries at build time. This has been the default since Angular 9.

## Just-in-Time (JIT)
In JIT, the Angular application is compiled in the browser during runtime, just before execution.

# Type Narrowing

Type narrowing reflects dynamic checks and predicates at runtime in the type-checker at compile time.

# Inject in Angular

@Inject is a parameter decorator in Angular used to resolve a token and inject a dependency into a constructor.

# Unit Testing in Angular

Angular unit testing involves testing small and isolated modules in your Angular application to ensure they work as expected.

# Jasmine and Karma

## Jasmine
Jasmine is a free and open-source Behavior Driven Development (BDD) framework for testing JavaScript code.

## Karma
Karma is a task runner that executes Jasmine test codes in multiple real-time browsers from the command line.

# Design Patterns

Design patterns are reusable solutions to common problems in software design.

# Design Patterns in Angular

- MVC Pattern
- Dependency Injection Pattern
- SOLID Pattern
- Strategy Pattern
- Visitor Pattern
- Singleton Pattern
- Factory Pattern

For more information on design patterns, visit [SourceMaking](https://sourcemaking.com/design_patterns).

# Difference between Subject and BehaviorSubject

## Subject
A Subject in RxJS does not hold a value and simply emits values to its subscribers.

### Example:
```javascript
const subject = new Rx.Subject();
subject.next(1);
subject.subscribe(x => console.log(x)); // Output: (nothing printed)
```

## BehaviorSubject example:

### Example:
```javascript
const subject = new Rx.BehaviorSubject(0);
subject.next(1);
subject.subscribe(x => console.log(x)); // Output: (1)
```

### Additional Notes

- **BehaviorSubject** should be created with an initial value: `new Rx.BehaviorSubject(1)`.
- Consider **ReplaySubject** if you want the subject to replay previously published values.

## Q. Difference between Subject and EventEmitter

- Use **EventEmitter** when transferring data from a child component to a parent component.
- Use **Subject** to transfer data between components regardless of their relationship.

## Q. Use of Subject and BehaviorSubject in Angular

The RxJS **Subject** and **BehaviorSubject** are unique observables that act as both observers and observables. They allow us to emit new values to the observable stream using the `next` method. All subscribers who subscribe to the subject will receive the same instance of the subject and hence the same values.
