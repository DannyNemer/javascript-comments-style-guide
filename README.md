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

  1. Use `//` for in-line comments. Place in-line comments on a newline above the corresponding source, and below an empty line.

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

  1. Phrase in-line comments in imperative present tense, and end with a period.

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

  1. Surround variable names and keywords with backticks.

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

  1. Use `/** ... */` for JSDoc blocks above functions and global variables. Include descriptions for the function, its parameters, and its return value, and specify types for all parameters and return values.

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

  1. Separate the function description from its tags with a blank line.

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

  1. Use lowercase for primitive data type names. In JavaScript, `'danny'` is not an instance of `String`, `true` is not an instance of `Boolean`, and `7` is not an instance of `Number`.

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

  1. Use title case for complex data type names: `Object`, `Array`, and `Function`.

    ```js
    // Bad
    /**
     ...
     * @param {object} The object to modify.
     * @param {function} The function invoked per iteration.
     * @returns {object} Returns the new object.
     */

    // Good
    /**
     ...
     * @param {Object} The object to modify.
     * @param {Function} The function invoked per iteration.
     * @returns {Object} Returns the new object.
     */
    ```

  1. Use `*` for mixed data types.

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

    // Bad
    /**
     ...
     * @returns {Array} Returns the string segments.
     */

    // Good
    /**
     ...
     * @returns {string[]} Returns the string segments.
     */
    ```

  1. Phrase function descriptions in indicative present tense.

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

  1. Reference function parameter names in the function's description.

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

  1. Surround names of optional parameters with brackets.

    ```js
    /**
     ...
     * @param {Function} [callback] The optional callback function.
     */
    ```

  1. If a parameter or return value can be of varying type, list all types, complex types before primitive types, separated by the `|` symbol.

    ```js
    // Bad
    /**
     ...
     * @param {*} predicate The function invoked per iteration.
     */

    // Bad - primitive types list before complex types
    /**
     ...
     * @param {string|Function|Object} predicate The function invoked per iteration.
     */

    // Good
    /**
     ...
     * @param {Function|Object|string} predicate The function invoked per iteration.
     */

    // Good
    /**
     ...
     * @returns {string|undefined} Returns the key of the matched element, else `undefined`.
     */
    ```

  1. If a parameter or return value can be of a type or an array of that type, list the non-array type first.

    ```js
    // Bad
    /**
     ...
     * @param {number[|number} indexes The indexes.
     */

    // Good
    /**
     ...
     * @param {number|number[]} indexes The indexes.
     */

    // Good
    /**
     ...
     * @param {...(number|number[])} indexes The indexes.
     */

    // Good
    /**
     ...
     * @param {...(Array|Array[]|Function|Function[]|Object|Object[]|string|string[])} iteratees The iteratees to invoke.
     */
    ```

  1. Begin descriptions for functions that perform checks and return a `boolean` with "Checks if `firstArg` ...".

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

    // Bad
    /**
     * Checks `value` is greater than `other`.
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

  1. Begin `boolean` `@param` descriptions with "Specify ..." and without conjunctions.

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

  1. List all options object proprieties with `@param` tags, including their default values, if any.

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

  1. Stylize the variadic argument types as `{...Type}`, with plural variable names, and surround the variable names in brackets to indicate optionality.

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
     * @return {string} Returns the padded string.
     */

    // Good
    /**
     ...
     * @returns {string} Returns the padded string.
     */
    ```

  1. Start every `@returns` description with "Returns ...".

    ```js
    // Bad
    /**
     ...
     * @returns {string} the padded string
     */

    // Good
    /**
     ...
     * @returns {string} Returns the padded string.
     */
    ```

#### `@example`

  1. Position `@example` blocks as the last tag within the comment block.

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

  1. Start `@example` blocks with a leading blank line.

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

  1. Below each exemplified operation in `@example` blocks, add an in-line comment that starts with "=>" followed by the operation's returned value.

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

  1. If an operation in an `@example` prints, add an in-line comment below the operation that starts with "=> Logs ...".

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