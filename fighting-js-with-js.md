# Fighting JavaScript with JavaScript

_Squarespace_

A talk on javascript architecture.

## A tale of JavaScript

**1994** - Webpages are just static HTML markup, Netscape only.

**Today** - Wide expansive ecosystems, many browser targets.

## Team Sizes

**Small single team**, fast iteration, simple ownership structure

**Multiple Teams** - Things are much more complicated, monolithic complex structure.



> Any complex system that works is anviariably found to have evolved forma s simple system that worked. A compelx system designed from sccratch never works and cannot be patched up to make it work. You ave to start over with a working simple system. 
>
> 
>
> *~ Gall's Law*



### Push

Splitting pieces into separate pieces in an architecture. Takes time, cannot happen overnight.

- Dependency Management
    - Break things into NPM modules
- Shared component library
    - Consistent UI
- Tracking
    - Becomes difficult to keep track of everything.
    - Alerts to track large size increases/decreases.
    - Optimize libraries last. Try to optimize for the application, rather than the individual libraries.
    - Track runtime metrics (time to load, documentReady, latency).
    - Speed kills - latency
        - **Google** - 100ms costs 4% in traffic.
        - **Amazon** - 100ms costs 1% decrease in sales.

## Pull

- Education and feedback (pipelines/dynamic feedback to engineers)

  - Lint the $%^& out of everything. Bad consistency is better than inconsistency.

    ```js
    // Lint error on build
    import { isNumber } from "lodash";

    // Good
    import isNumber from "lodash/isNumber";
    ```

  - Not every tool comes in the box. At some point you will need custom rules, write custom ones. Write custom lint rules to enforce things like this.

  ```js
  // No good
  delete window.some_prop

  // Go ahead
  try {
      delete window.some_prop
  } catch (e) {
      // handle error
  }
  ```

- What is an AST (abstract syntax tree)

  - Used to tokenize/parse javascript for ESLint/Babel.
  - Common AST's : Acord, Esprima
  - Used to write custom lint rules.

## Mechanics (refactoring) 

Example: refactor every string literal to wrapped in a translate function.

- Use JSCodeShift to convert the item using an AST.
- Very testable.
- Much less manual than find/replace or regex.



Example: keep code in the code-base is used internally, not in production. 

- Write a babel transform to strip out the unwanted pieces in the build.

## Invest Into Scale



Custom webpack wrapper as a build tool!!!