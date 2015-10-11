# JavaScript Comments Style Guide
The very early beginnings of a JavaScript comments style guide.


## In-Line Comments
  1. Use `/** ... */` for JSDoc above functions and global variables. Include descriptions for the function, its paramters, and its return value, and specify types for all parameters and return values.

    ```js
    // Bad
    // Replaces `'~'` in `path` with the home directory path.
    //
    // @param {string} path The file path.
    // @returns {string} Returns `path` with `'~'` replaced with the home directory.
    dantil.expandHomeDir = function (path) {

      // ...stuff...

      return modifedPath
    }

    // Good
    /**
     * Replaces `'~'` in `path` with the home directory path.
     *
     * @param {string} path The file path.
     * @returns {string} Returns `path` with `'~'` replaced with the home directory.
     */
    dantil.expandHomeDir = function (path) {

      // ...stuff...

      return modifedPath
    }
    ```

  1. Use `//` for in-line comments. Place in-line comments on a newline above the subject of the comment. Put an empty line before the comment.

    ```js
    // Bad
    var myObject = {}
    set(myObject, 'prop', 'val') // Set the value of 'prop' to 'val'.

    // Still bad
    var myObject = {}
    // Set the value of 'prop' to 'val'.
    set(myObject, 'prop', 'val')

    // Good
    var myObject = {}

    // Set the value of 'prop' to 'val'.
    set(myObject, 'prop', 'val')
    ```

  1. Write in-line comments in imperative present tense. End in-line comments with a period.

    ```js
    // Bad
    // Sets the value of 'prop' to 'val'
    set(myObject, 'prop', 'val')

    // Still bad
    // Set the value of 'prop' to 'val'
    set(myObject, 'prop', 'val')

    // Good
    // Set the value of 'prop' to 'val'.
    set(myObject, 'prop', 'val')
    ```

  1. Use backticks for all references to variables or keywords.

    ```js
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

## JSDoc
  1. End every description with a period.
  1. Separate every element with a single space - do not align elements.
  1. Separate the function description from the tags with a blank line.
  1. Lead with tags without arguments (e.g., `@private`, `@static`).
  1. Use lowercase for labels of primitive data types. In JavaScript, `'danny'` is not an instance of `String`, `true` is not an instance of `Boolean`, and `7` is not an instance of `Number`.

    ```js
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

    ```js
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

    ```js
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

    ```js
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

    ```js
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

    ```js
    /**
     * @param {Function} [callback] The optional callback function.
     */
    ```

  1. If a parameter or return value is of variadic type, list the types with the `|` symbol.
    ```js
    // Bad
    /**
     * @param {*} predicate The function invoked per iteration.
     */

    // Good
    /**
     * @param {Function|Object|string} predicate The function invoked per iteration.
     */
    ```

#### `@returns`
  1. Use `@returns` instead of `@return`.

    ```js
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

    ```js
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

    ```js
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

    ```js
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

    ```js
    // Bad
    /**
     * @type {Array}
     */

    // Good
    /**
     * @type Array
     */
    ```