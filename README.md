# JavaScript Comments Style Guide
The very early beginnings of a JavaScript comments style guide.


## In-Line Comments
  1. In-line comments should always be `//` and never comment blocks (`/***/`).
  1. Comments above functions and global variables should always use comment blocks (`/***/`) and JSDoc.
  1. Place in-line comments above the line of code, never on the same line.

    ```javascript
    // Bad
      myFunction(2) // Does stuff

    // Good
      // Does stuff
      myFunction(2)
    ```

  1. End in-line comments with a period.
  1. Write in-line comments in imperative present tense.

    ```javascript
    // Bad
      // Gets the thing.
      myFunction(2)

    // Good
      // Get the thing.
      myFunction(2)
    ```

  1. Insert a blank line above in-line comments.

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

## JSDoc
  1. End every description with a period.
  1. Separate every element with a single space - do not align elements.
  1. Separate the function description from the tags with a blank line.
  1. Lead with tags without arguments (e.g., `@private`, `@static`).
  1. Use lowercase for primitive data types. In JavaScript, `'danny'` is not an instance of `String`. Some applies of `true` and `Boolean`, and `7` and `Number`.

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

  1. Use `*` for mixed datatypes (not `Mixed`).

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

  1. Write function descriptions in indicative present sense.
  1. Variadic arguments should have as their type: `{...Type}` and be given a plural name: values, arrays.

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

  1. Use backticks for all references to variables or keywords.

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

  1. Reference function parameters names in the function's description.
  1. Begin `@param` descriptions with "The ..."
  1. Surround optional parameters with brackets.

    ```javascript
    /**
     * @param {Function} [callback] The optional callback function.
     */
    ```

### `@returns`
  1. Use `@returns` instead of `@return`.

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

  1. Start every `@returns` description with "Returns ...".

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
  1. If including an `@example`, it must be the last tag within the comment block.
  1. Start an `@example` with a leading blank line.
  1. In `@example` block, comment the output of a function with a comment line below and a "=>".

    ```javascript
    // Bad
    /**
     * @example
     *
     * // Returns `true`
     * dantil.arraysEqual([], [])
     */

    // Good
    /**
     * @example
     *
     * dantil.arraysEqual([], [])
     * // => true
     */
  ```

  1. If something prints in a `@example`, put an in-line comment within the example like #7, but say "Logs...".

    ```javascript
    /**
     * @example
     *
     * dantil.logError('what?')
     * // => Logs "Error: what?"
     */
    ```

### `@type`
  1. Tag variable type without brackets

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