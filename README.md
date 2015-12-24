# JavaScript Comments Style Guide
The beginnings of a JavaScript comments style guide.

## Table of Contents

  1. [In-Line Comments](#in-line-comments)
  1. [JSDoc](#jsdoc)
    1. [`@param`](#param)
    1. [`@returns`](#returns)
    1. [`@example`](#example)
    1. [`@type`](#type)

## In-Line Comments

  1. Use `/** ... */` for JSDoc above functions and global variables. Include descriptions for the function, its parameters, and its return value, and specify types for all parameters and return values.

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

  1. Use backticks for variable names and keywords.

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
     ...
     * @param {Object} schema The definitions of properties for 'options'.
     * @param {Object} options The options object to check.
     * @returns {boolean} Returns true if 'options' is ill-formed, else false.
     */

    // Good
    /**
     ...
     * @param {Object} schema The definitions of properties for `options`.
     * @param {Object} options The options object to check.
     * @returns {boolean} Returns `true` if `options` is ill-formed, else `false`.
     */
    ```

## JSDoc

  1. End every description with a period.

    ```js
    // Bad
    /**
     * Converts `string` to camel case
     *
     * @param {string} string The string to convert
     * @returns {string} Returns the camel cased string
     */

    // Good
    /**
     * Converts `string` to camel case.
     *
     * @param {string} string The string to convert.
     * @returns {string} Returns the camel cased string.
     */
    ```

  1. Separate every element with a single space; do not align elements.

    ```js
    // Bad
    /**
     ...
     * @param {string}   filePath   The path of the source file to search.
     * @param {*}        value      The value to search for.
     * @param {boolean}  stringify  Specify converting `value` to a string
     *   representation before searching.
     */

    // Good
    /**
     ...
     * @param {string} filePath The path of the source file to search.
     * @param {*} value The value to search for.
     * @param {boolean} stringify Specify converting `value` to a string
     *   representation before searching.
     */
    ```

  1. Separate the function description from the tags with a blank line.

    ```js
    // Bad
    /**
     * Stringifies and writes `obj` to a JSON file at `path`.
     * @param {string} path The file path to write to.
     * @param {Object} obj The object to save to `path`.
     */

    // Good
    /**
     * Stringifies and writes `obj` to a JSON file at `path`.
     *
     * @param {string} path The file path to write to.
     * @param {Object} obj The object to save to `path`.
     */
    ```

  1. Lead with tags without arguments (e.g., `@private`, `@static`), then tags without descriptions (e.g., `@memberof`), and always end with `@example`, if any.

    ```js
    // Bad
    /**
     * Removes any extraneous digits from `number`, which result from operations
     * limited by JavaScript's floating point number precision.
     *
     * @param {number} number The number to rid of any extraneous digits.
     * @returns {number} Returns the cleaned number.
     * @memberOf dantil
     * @category Number
     * @static
     * @example
     *
     * var number = 0.1 * 0.2
     * // => 0.020000000000000004
     *
     * number = dantil.cleanFloat(number)
     * // => 0.02
     */

    // Good
    /**
     * Removes any extraneous digits from `number`, which result from operations
     * limited by JavaScript's floating point number precision.
     *
     * @static
     * @memberOf dantil
     * @category Number
     * @param {number} number The number to rid of any extraneous digits.
     * @returns {number} Returns the cleaned number.
     * @example
     *
     * var number = 0.1 * 0.2
     * // => 0.020000000000000004
     *
     * number = dantil.cleanFloat(number)
     * // => 0.02
     */
    ```

  1. Use lowercase for labels of primitive data types. In JavaScript, `'danny'` is not an instance of `String`, `true` is not an instance of `Boolean`, and `7` is not an instance of `Number`.

    ```js
    // Bad
    /**
     ...
     * @param {String} string The string to check.
     * @param {Number} number The number to check.
     * @returns {Boolean} Returns `true` if `string` is equal to `number`.
     */

    // Good
    /**
     ...
     * @param {string} string The string to check.
     * @param {number} number The number to check.
     * @returns {boolean} Returns `true` if `string` is equal to `number`.
     */
    ```

  1. Use uppercase for labels of complex data types: `Object`, `Array`, and `Function`.

    ```js
    // Bad
    /**
     ...
     * @param {array} The array to modify.
     * @param {function} The function invoked per iteration.
     * @returns {array} Returns the new object.
     */

    // Good
    /**
     ...
     * @param {Array} The array to modify.
     * @param {Function} The function invoked per iteration.
     * @returns {Array} Returns the new object.
     */
    ```

  1. Use `*` for mixed data types (not `Mixed`).

    ```js
    // Bad
    /**
     ...
     * @returns {Mixed} Returns the return value of `callback`.
     */

    // Good
    /**
     ...
     * @returns {*} Returns the return value of `callback`.
     */
    ```

  1. Style the type name for `Array` values as the type of the array's contents followed by empty brackets.

    ```js
    // Bad
    /**
     ...
     * @param {Array} strings The strings to concatenate.
     */

    // Good
    /**
     ...
     * @param {string[]} strings The strings to concatenate.
     */
    ```

  1. Write function descriptions in indicative present tense.

    ```js
    // Bad
    /**
     * Create a function that memoizes the result of `func`.
     */

    // Good
    /**
     * Creates a function that memoizes the result of `func`.
     */
    ```

  1. Include function parameter names in the function's description.

    ```js
    // Bad
    /**
     * Create a function that memoizes the result of the provided function.
     *
     * @param {Function} func The function to curry.
     */

    // Good
    /**
     * Creates a function that memoizes the result of `func`.
     *
     * @param {Function} func The function to curry.
     */
    ```

  1. Surround optional parameters with brackets.

    ```js
    /**
     ...
     * @param {Function} [callback] The optional callback function.
     */
    ```

  1. If a parameter or return value is of variadic type, list the types with the `|` symbol.

    ```js
    // Bad
    /**
     ...
     * @param {*} predicate The function invoked per iteration.
     */

    // Good
    /**
     ...
     * @param {Function|Object|string} predicate The function invoked per iteration.
     */
    ```

  1. Begin descriptions for functions which perform checks or validations and return a `boolean` with "Checks if `firstArg` ...".

    ```js
    // Bad
    /**
     * Determines if `value` is greater than `other`.
     ...
     */

    // Bad
    /**
     * Checks whether `value` is greater than `other`.
     ...
     */

    // Good
    /**
     * Checks if `value` is greater than `other`.
     *
     * @param {number} value The number to compare.
     * @param {number} other The other number to compare.
     * @returns {Boolean} Returns `true` if `value` is greater than `other`, else `false`.
     */
    ```

#### `@param`

  1. Begin non-`boolean` `@param` descriptions with "The ...".

    ```js
    // Bad
    /**
     ...
     * @param {string} path Where to write `stdout`.
     * @param {Function} func Processed while writing output to `path`.
     * @returns {*} Returns the value returned by `func`, if any.
     */

    // Good
    /**
     ...
     * @param {string} path The path where to write `stdout`.
     * @param {Function} func The function to process while writing output to `path`.
     * @returns {*} Returns the value returned by `func`, if any.
     */
    ```

  1. Begin `@param` descriptions of type `boolean` with "Specify ..." and without conjunctions.

    ```js
    // Bad
    /**
     ...
     * @param {boolean} isSorted Specifies the array is sorted.
     */

    // Bad - do not use conjunctions (e.g., "whether", "if")
    /**
     ...
     * @param {boolean} isSorted Specify whether the array is sorted.
     * @param {boolean} isMutable Specify if the array array is mutable.
     */

    // Good
    /**
     ...
     * @param {boolean} isSorted Specify the array is sorted.
     * @param {boolean} leading Specify invoking on the leading edge of the timeout.
     */
    ```

  1. List all proprieties of an options object with `@param` tags, including their default values, if any.

    ```js
    // Bad
    /**
     ...
     * @param func {Function}: The function to debounce.
     * @param [options] {Object}: The options object.
     */

    // Good
    /**
     ...
     * @param func {Function}: The function to debounce.
     * @param [options] {Object}: The options object.
     * @param [options.leading=false] {boolean}: Specify invoking on the leading edge
     *   of the timeout.
     * @param [options.maxWait] {number}: The maximum time `func` is allowed to be
     *   delayed before it’s invoked.
     * @param [options.trailing=true] {boolean}: Specify invoking on the trailing
     *   edge of the timeout.
     */
    ```

  1. Stylize the type of variadic arguments as `{...Type}`, use plural variable names, and surround variable names in brackets to indicate optionality.

    ```js
    // Bad
    /**
     ...
     * @param {...string} stringN The strings to concatenate.
     */

    // Bad
    /**
     ...
     * @param {...string} string [, stringN] The values to print.
     */

    // Still bad
    /**
     ...
     * @param {...string} strings The strings to concatenate.
     */

    // Good
    /**
     ...
     * @param {...string} [strings] The strings to concatenate.
     */
    ```

#### `@returns`

  1. Use `@returns` instead of `@return`.

    ```js
    // Bad
    /**
     ...
     * @return array Returns the new array.
     */

    // Good
    /**
     ...
     * @returns array Returns the new array.
     */
    ```

  1. Start every `@returns` description with "Returns ...".

    ```js
    // Bad
    /**
     ...
     * @returns array The new array.
     */

    // Good
    /**
     ...
     * @returns array Returns the new array.
     */
    ```

#### `@example`

  1. Position an `@example` as the last tag within the comment block.

    ```js
    /**
     * Replaces `'~'` in `path` (if present and at the path's start) with the home
     * directory path.
     *
     * @static
     * @memberOf dantil
     * @category File System
     * @param {string} path The file path.
     * @returns {string} Returns `path` with `'~'`, if present, replaced with the
     *   home directory path.
     * @example
     *
     * dantil.expandHomeDir('~/Desktop')
     * // => '/Users/Danny/Desktop'
     */
    ```

  1. Start an `@example` with a leading blank line.

    ```js
    // Bad
    /**
     ...
     * @example
     * dantil.expandHomeDir('~/Desktop')
     * // => '/Users/Danny/Desktop'
     */

    // Good
    /**
     ...
     * @example
     *
     * dantil.expandHomeDir('~/Desktop')
     * // => '/Users/Danny/Desktop'
     */
    ```

  1. In `@example` block, comment the output of a function with a comment line below and a "=>".

    ```js
    // Bad
    /**
     ...
     * @example
     *
     * // Returns `true`
     * dantil.arraysEqual([], [])
     */

    // Good
    /**
     ...
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
     ...
     * @example
     *
     * dantil.logError('what?')
     * // => Prints "Error: what?"
     */

    // Good
    /**
     ...
     * @example
     *
     * dantil.logError('what?')
     * // => Logs "Error: what?"
     */
    ```

#### `@type`

  1. Do not surround data type names of `@type` tags (for global variables) with brackets.

    ```js
    // Bad
    /**
     ...
     * @type {Array}
     */

    // Good
    /**
     ...
     * @type Array
     */
    ```