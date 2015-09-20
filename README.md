# JavaScript Comments Style Guide
The very early beginnings of a JavaScript comments style guide.


## In-Line Comments
  1. In-line comments should always be `//` and never comment blocks (`/***/`).
  1. Comments above functions and global variables should always use comment blocks (`/***/`) and JSDoc.
  1. Use backticks for all references to variables or keywords.

    ```javascript
    // Bad
    // Checks if options is ill-formed.
    dantil.illFormedOpts(schema, options)

    // Bad
    // Checks if 'options' is ill-formed.
    dantil.illFormedOpts(schema, options)

    // Good
    // Checks if `options` is ill-formed.
    dantil.illFormedOpts(schema, options)

    // Bad
    /**
     * @param {Object} schema The definitions of properties for 'options'.
     * @param {Object} options The options object to check.
     * @returns {boolean} Returns true if 'options' is ill-formed, else false.
     */

    // Good
    /**
     * @param {Object} schema The definitions of properties for `options`.
     * @param {Object} options The options object to check.
     * @returns {boolean} Returns `true` if `options` is ill-formed, else `false`.
     */
    ```

  1. Place in-line comments above the line of code, never on the same line.

    ```javascript
    // Bad
    set(myObject, 'prop', 'val') // Set the value of 'prop' to 'val'.

    // Good
    // Set the value of 'prop' to 'val'.
    set(myObject, 'prop', 'val')
    ```

  1. Write in-line comments in imperative present tense.

    ```javascript
    // Bad
    // Sets the value of 'prop' to 'val'.
    set(myObject, 'prop', 'val')

    // Good
    // Set the value of 'prop' to 'val'.
    set(myObject, 'prop', 'val')
    ```

  1. End in-line comments with a period.

    ```javascript
    // Bad
    // Set the value of 'prop' to 'val'
    set(myObject, 'prop', 'val')

    // Good
    // Set the value of 'prop' to 'val'.
    set(myObject, 'prop', 'val')
    ```

  1. Insert a blank line above in-line comments.

    ```javascript
    // Bad
    var myObject = {}
    // Set the value of 'prop' to 'val'.
    set(myObject, 'prop', 'val')

    // Good
    var myObject = {}

    // Set the value of 'prop' to 'val'.
    set(myObject, 'prop', 'val')
    ```

## JSDoc
  1. End every description with a period.
  1. Separate every element with a single space - do not align elements.
  1. Separate the function description from the tags with a blank line.
  1. Lead with tags without arguments (e.g., `@private`, `@static`).
  1. Use lowercase for labels of primitive data types. In JavaScript, `'danny'` is not an instance of `String`, `true` is not an instance of `Boolean`, and `7` is not an instance of `Number`.

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

  1. Use uppercase for labels of complex data types: `Object`, `Array`, and `Function`.

    ```javascript
    // Bad
    /**
     * @param {array} The array to modify.
     * @param {function} The function invoked per iteration.
     * @returns {array} Returns the new object.
     */

    // Good
   /**
    * @param {Array} The array to modify.
    * @param {Function} The function invoked per iteration.
    * @returns {Array} Returns the new object.
    */
    ```

  1. Use `*` for mixed data types (not `Mixed`).

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

  1. Variadic arguments should have as their type: `{...Type}` and be given a plural name: values, arrays.

    ```javascript
    // Bad
    /**
     * @param {...string} stringN The strings to concatenate.
     */

    // Bad
    /**
     * @param {...string} string [, stringN] The values to print.
     */

    // Good
    /**
     * @param {...string} strings The strings to concatenate.
     */
    ```

  1. Style the type name for `Array` values as the type of the array's contents followed by empty brackets.

    ```javascript
    // Bad
    /**
     * @param {Array} strings The strings to concatenate.
     */

    // Good
    /**
     * @param {string[]} strings The strings to concatenate.
     */
    ```

  1. Write function descriptions in indicative present tense.

  1. Reference function parameter names in the function's description.
  1. Begin `@param` descriptions with "The ...".
  1. Surround optional parameters with brackets.

    ```javascript
    /**
     * @param {Function} [callback] The optional callback function.
     */
    ```

#### `@returns`
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

#### `@example`
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
    // Bad
    /**
     * @example
     *
     * dantil.logError('what?')
     * // => Prints "Error: what?"
     */

    // Good
    /**
     * @example
     *
     * dantil.logError('what?')
     * // => Logs "Error: what?"
     */
    ```

#### `@type`
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