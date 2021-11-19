# WORK IN PROGRESS, DON'T USE YET
# So you want to contribute to my repositories?
That's great! Welcome aboard :)

Before you begin though please read the following styleguides to make sure we keep the project repositories consistent and high quality!

###### Note: the code examples here will be in nodejs syntax, since that's what I work with mostly. However if any other languages are to occur in my projects you should still follow these styleguides, unless an exception for the specific language is specified.

# Styleguides

## Index
- [Commits](#commits)
	- [Titles](#titles)
	- [Descriptions](#descriptions)
- [Code](#code)
	- [Variables](#variables)
	- [Comments](#comments)
- [Linting](#linting)


## Commits
###### Note for my CLI git friends: "commit title" is the fist line of a commit message, "commit description" is the rest of it.

### Titles
- Commit titles should contain a short, general description of the *effect* of the changes.  
	*(E.g. ``Fix startup bug`` instead of ``Update app.js``)*
- Use present tense for titles.

### Descriptions
- Put a more detailed explanation of the changes the commit in the description. The more detail, the better.
	- Descriptions are not required for simple changes that are already explained in the title.
- Always mention any relevant issues or pull requests to the commit in the description.

## Code
### Naming
###### Note: Guidelines mentioning "names" in this section are applicable to all names (variables, functions etc.), unless otherwise specified.
- Use `camelCase` for variables and functions, `UPPER_CASE_SNAKE_CASE` for constants and `PascalCase` for classes.
	```node
	let exampleVar;
	const EXAMPLE_CONST;
	function exampleFunc() {}
	class ExampleClass {}
	```
- Use descriptive names, with the exception of `i` for index variables in loops.
	```node
	const ddmmyyyy = new Date().toDateString();    // Bad
	const currentDate = new Date().toDateString(); // Good
	```
- Capitalise abbreviations in names.
	```node
	function getID() {}
	let websiteURI;
	```
- ***Never*** use negation for boolean variable names.
	```node
	// Bad
	let hasNotLoaded = true;
	// Good
	let hasLoaded = false;
	```
- Use prefixes like ``is`` or ``has`` for boolean variable names.
	```node
	let isDone = false;
	let hasBegun = true;
	```
- Use underscore for unused callback function parameter names.
	```node
	functionWithCallback((_, variable) => { /* Do stuff */ });
	```  

### Braces, brackets & parentheses
- Use inline bracing style (OTBS).
	```node
	if (condition) {
		// Do stuff
	} else {
		// Do other stuff
	}
	```
- Always use braces around blocks of code, even single statements.
	```node
	// Bad
	if (condition) return;
	// Good
	if (condition) { 
		return; 
	}
	if (condition) { return; }
	```
- Put spaces before opening braces/brackets/parentheses.
	```node
	if (condition) {
		let arr = [1, 2, 3];
	}
	```
- Put spaces in braces/brackets of inline code blocks or small object literals in arrays.
	```node
	if (condition) { return; }
	let arrayOfObjects = [
		{ key: value },
		{ key: value }
	];
	```
- Put spaces around operators.
	```node
	// Bad
	let one=(1+1)/2
	// Good
	let one = (1 + 1) / 2
	```
- Wrap boolean conditional assignments in parentheses to differentiate from shorthand.
	```node
	// Bad
	let value = truthyValue || falsyValue;
	// Good
	let value = (truthyValue || falsyValue);
	```
- Prefer ``if () { return; }`` over massive ``else {}`` blocks.
	```node
	// Bad
	function doStuff() {
		if (truthyValue) {
			// Do the stuff
		} else {
			// Do 100+ lines of other stuff
		}
	}
	// Good
	function doStuff() {
		if (truthyValue) {
			// Do the stuff
			return;
		}
		// Do 100+ lines of other stuff
	}
	```

### Values

### Variables
- Always use ``const`` and ``let``. Never use ``var``.  
- Indicate unused callback function variables with an underscore (``_``).
	```node
	getSomething((_, value) => doStuffWithSomething(value));
	```
- Use constants for variables of which the purpose isn't self-explanatory
	```node
	// Bad
	setTimeout(blastOff, 86400000);
	// Good
	const MILLISECONDS_IN_A_DAY = 60 * 60 * 24 * 1000; //86400000
	setTimeout(blastOff, MILLISECONDS_IN_A_DAY);
	```
- Use numeric seperators for large numbers.
	```node
	let largeNumber = 12_345_678;
	```
- Use double quotes for strings facing the front-end (strings the user might see).
- Use single quotes for all other strings.



### Comments
- ***Never*** leave commented out code in a commit.
- Only provide comments where the code isn't strictly self-explanatory.  
	*(So no journal or positional marker comments either)*
- Put a space between the comment and its indicator, and between the indicator and the code for inline comments.  
	*(E.g. ``// Comment`` instead of ``//Comment``)*
- Comment block indicators are allowed for very large comments, but per-line indicators are preferred.
- Comments should be in proper english.
- Use proper capitalisation, spelling, grammar and punctuation.
	- Punctuation at the end of a comment can be ommited if it's not used for an abbreviation.
- Usage of common abbriaviations is allowed, but use proper punctuation with them.  
	*(E.g. ``e.g.``, ``etc.`` etc.)*
- References to code should be wrapped in graves (`` ` ``).  
	*(E.g. ``// Referencing function `doStuff()` from the code``)*
- Comments relating to a block of code should be placed on the line above it.  
	Comments relating to one line of code should be placed inline.  
	```node
	// Reference block of code
	doStuff();
	doMoreStuff() // Reference line of code
	```
	
## Linting
- Using a linter when adding code isn't strictly necessary, but it is *highly* encouraged.
- A default settings file for each linter used is provided under the [linter settings folder](/linter%20settings).
- A table of language, linter used and it's settings file:
<ul>
	
| Language | linter | settings file |
| --- | --- | --- |
| Node.js | jshint | ``/.jshintrc`` |
| JS | jshint | ``/.jshintrc`` |
</ul>
