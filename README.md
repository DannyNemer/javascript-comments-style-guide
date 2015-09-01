# JavaScript Style Guide
The early beginings of a JavaScript style guide.

1. Inline comments should always be "//" and never comment blocks ("/***/")
2. Comments above functions and global variables should always use comment blocks ("/***/") and JSDoc
3. Inline comments should always be above the line of code, never on the same line.
	```javascript
	// Bad
		myFunction(2) // Does stuff

	// Good
		// Does stuff
		myFunction(2)
	```
4. Inline comments should be imperative present tense and end with a period.
	```javascript
	// Bad
		// Gets the thing
		myFunction(2)

	// Good
		// Get the thing.
		myFunction(2)
	```
5. There should always be a blank line above inline comments
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
6. Always use a space after keywords, including "if" and "else"
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
7. Never use a space between a function definition's name and the left parenthsis. Needs to resemble how it is used. Spaces are used to seperate keywords.
	```javascript
	// Bad
	function dance (param) {}

	// Good
	function dance(param) {}
	```
8. Never use spaces inside parentheses:
	```javascript
	// Bad
	if ( true ) {}

	// Good
	if (true) {}
	```

## JSDoc
1. Use "@returns" instead of "@return"
2. Start an @example with a leading blank line
3. Start every @returns description with "Returns ..."
4. End every description with a period
5. Seperate every element with a single space - do not align elements
6. Seperate the function description from the tages with a blank line
7. In "@example" block, comment the output of a function with a comment line below and a "=>":
	```javascript
	/**
	 * @example
	 *
	 * dantil.arraysEqual([], [])
	 * // => true
	 */
	```

8. If something prints in a @example, put an inline comment within the example like #7, but say "Logs..."
	```javascript
	/**
	 * @example
	 *
	 * dantil.logError('what?')
	 * // => Logs "Error: what?"
	 */
	```

9. Lead with tags without arguments (e.g., @private, @static)
10. Use lowercase for primitive data types (e.g., number, boolean, string)
11. Use "*" for mixed datatypes (not "Mixed")
12. All function descriptions should be indicative present sense
13. Vardiac arguments should have as there type: {...Type} and be given a plural name: values, arrays
14. Tag variable type without brackets
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
15. Use backticks for all references to variables or keywords
16. Reference function paramters names in the function's description
17. Begin @param descriptions with "The ..."