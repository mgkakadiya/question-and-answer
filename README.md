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


