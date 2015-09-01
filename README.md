# JavaScript Style Guide
The very early beginnings of a JavaScript style guide.


## Table of Contents

  1. [JavaScript](#javascript)
  1. [JSDoc](#jsdoc)
    1. [`@returns`](#returns)
    1. [`@example`](#example)
    1. [`@type`](#type)

## JavaScript

- [1.1](#1.1) <a name='1.1'></a> In-line comments should always be `//` and never comment blocks (`/***/`).
- [1.2](#1.2) <a name='1.2'></a> Comments above functions and global variables should always use comment blocks ("/***/") and JSDoc.
- [1.3](#1.3) <a name='1.3'></a> In-line comments should always be above the line of code, never on the same line.

  ```javascript
  // Bad
    myFunction(2) // Does stuff

  // Good
    // Does stuff
    myFunction(2)
  ```

- [1.4](#1.4) <a name='1.4'></a> In-line comments should be imperative present tense and end with a period.

  ```javascript
  // Bad
    // Gets the thing
    myFunction(2)

  // Good
    // Get the thing.
    myFunction(2)
  ```

- [1.5](#1.5) <a name='1.5'></a> There should always be a blank line above in-line comments.

  ```javascript
  // Bad
    var thing = getMe()
    // My comment
    return thing.pop()

  // Good
    var thing = getMe()

    // My comment
    return thing.pop()
  ```

- [1.6](#1.6) <a name='1.6'></a> Always use a space after keywords, including `if` and `else`.

  ```javascript
  // Bad
  if(num > 2) {}

  // Bad
  while(true){}

  // Good
  if (num > 2) {}

  // Good
  while (true) {}
  ```

- [1.7](#1.7) <a name='1.7'></a> Never use a space between a function definition's name and the left parenthesis. Needs to resemble how it is used. Spaces are used to separate keywords.

  ```javascript
  // Bad
  function dance (param) {}

  // Good
  function dance(param) {}
  ```

- [1.8](#1.8) <a name='1.8'></a> Never use spaces inside parentheses.

  ```javascript
  // Bad
  if ( true ) {}

  // Good
  if (true) {}
  ```

## JSDoc
- [2.1](#2.1) <a name='2.1'></a> End every description with a period.
- [2.2](#2.2) <a name='2.2'></a> Separate every element with a single space - do not align elements.
- [2.3](#2.3) <a name='2.3'></a> Separate the function description from the tags with a blank line.
- [2.4](#2.4) <a name='2.4'></a> Lead with tags without arguments (e.g., `@private`, `@static`).
- [2.5](#2.5) <a name='2.5'></a> Use lowercase for primitive data types. In JavaScript, `'danny'` is not an instance of `String`. Some applies of `true` and `Boolean`, and `7` and `Number`.

  ```javascript
  // Bad
  /**
   * @param {String} string The string to check.
   * @param {Number} number The number to check.
   * @returns {Boolean} Returns `true` if `string` is equal to `number`.
   */

  // Good
  /**
   * @param {string} string The string to check.
   * @param {number} number The number to check.
   * @returns {boolean} Returns `true` if `string` is equal to `number`.
   */
  ```

- [2.6](#2.6) <a name='2.6'></a> Use "*" for mixed datatypes (not `Mixed`).

  ```javascript
  // Bad
  /**
   * @returns {Mixed} Returns the return value of `callback`.
   */

  // Good
  /**
   * @returns {*} Returns the return value of `callback`.
   */
  ```

- [2.7](#2.7) <a name='2.7'></a> All function descriptions should be indicative present sense.
- [2.8](#2.8) <a name='2.8'></a> Variadic arguments should have as their type: `{...Type}` and be given a plural name: values, arrays.

  ```javascript
  // Bad
  /**
   * @param {...String} stringN The strings to concatenate.
   */

  // Bad
  /**
   * @param {...String} string [, stringN] The values to print.
   */

  // Good
  /**
   * @param {...String} strings The strings to concatenate.
   */
  ```

- [2.9](#2.9) <a name='2.9'></a> Use backticks for all references to variables or keywords.

  ```javascript
  // Bad
  /**
   * Converts myString to lowercase.
   *
   * @param {String} myString The string to convert to lowercase.
   */

  // Bad
  /**
   * Converts `myString` to lowercase.
   *
   * @param {String} myString The string to convert to lowercase.
   */
  ```

- [2.10](#2.10) <a name='2.10'></a> Reference function parameters names in the function's description.
- [2.11](#2.11) <a name='2.11'></a> Begin `@param` descriptions with "The ..."
- [2.12](#2.11) <a name='2.12'></a> Surround optional parameters with brackets.

  ```javascript
  /**
   * @param {Function} [callback] The optional callback function.
   */
  ```

### `@returns`
- [2.1.1](#2.1.1) <a name='2.1.1'></a> Use `@returns` instead of `@return`.

  ```javascript
  // Bad
  /**
   * @return array Returns the new array.
   */

  // Good
  /**
   * @returns array Returns the new array.
   */
  ```

- [2.1.2](#2.1.2) <a name='2.1.2'></a> Start every `@returns` description with "Returns ...".

  ```javascript
  // Bad
  /**
   * @returns array The new array.
   */

  // Good
  /**
   * @returns array Returns the new array.
   */
  ```

### `@example`
- [2.2.1](#2.2.1) <a name='2.2.1'></a> Start an `@example` with a leading blank line.
- [2.2.2](#2.2.2) <a name='2.2.2'></a> In `@example` block, comment the output of a function with a comment line below and a "=>".

  ```javascript
  /**
   * @example
   *
   * dantil.arraysEqual([], [])
   * // => true
   */
  ```

- [2.2.3](#2.2.3) <a name='2.2.3'></a> If something prints in a `@example`, put an in-line comment within the example like #7, but say "Logs...".
  ```javascript
  /**
   * @example
   *
   * dantil.logError('what?')
   * // => Logs "Error: what?"
   */
  ```

### `@type`
- [2.3.1](#2.3.1) <a name='2.3.1'></a> Tag variable type without brackets

  ```javascript
  // Bad
  /**
   * @type {Array}
   */

  // Good
  /**
   * @type Array
   */
  ```