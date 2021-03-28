# So you want to contribute to my repositories?
That's great! Welcome aboard :)

Before you begin though please read the following styleguides to make sure we keep the project repositories consistent and high quality!

###### Note: the code examples here will be in nodejs syntax, since that's what I work with mostly. However if any other languages are to occur in my projects you should still follow these styleguides, unless an exception for the specific language is specified.

## Index
- [Commits](#commits)
  - [Titles](#titles)
  - [Descriptions](#descriptions)
- [Code](#code)
  - [Variables](#variables)
  - [Comments](#comments)
- [Linting](#linting)

## Styleguides

### Commits

###### Note for my CLI git friends: "commit title" is the fist line of a commit message, "commit description" is the rest of it.

#### Titles
- Commit titles should contain a short, general description of the *effect* of the changes.  
  *(E.g. ``Fix startup bug`` instead of ``Update app.js``)*
  - If this isn't possible for any reason, commit titles should contain a short, general description of the action performed.  
  *(E.g. ``Add settings file``)*
- Commit titles should always be in present tense.

#### Descriptions
- Commit descriptions should contained an explaination of every change in the commit. More detail is better.
  - Commit descriptions are not required for simple changes for which the commit title provides enough explanation.
- Commit descriptions should mention any relevant issues/pull requests.

## Code
- Use inline braces.
- Always use braces.
- Prefer inline code for one line code blocks, objects with one entry or arrays with a small number of entries. Prefer expanded code for all other cases.
- Put spaces in braces/brackets of inline code blocks or objects.
  ```node
  if (isTrue) { return; }
  
  let array = [1, 2, 3];
  let object = {a:1, b:2};
  
  let arrayOfObjects = [
    { key: value },
    { key2: value2 }
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

### Variables
- Always use ``const`` and ``let``. Never use ``var``.  
- Use descriptive variable names.  
  - This also goes for ``for of``, ``forEach`` etc. loop parameters, with the exception of ``i`` for index.
  ```node
  // Bad
  const ddmmyyyy = new Date().toDateString();
  // Good
  const currentDate = new Date().toDateString();
  ```
- Indicate unused callback function variables with an underscore (``_``).
  ```node
  getSomething((_, value) => doStuffWithSomething(value));
  ```
- Use camelCase for normal variables.
- Use UPPER_CASE_SNAKE_CASE for constants.
- Use constants for variables of which the purpose isn't self explanatory
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
- Use prefixes like ``is`` or ``has`` for boolean variable names.
  ```node
  let isDone = false;
  let hasBegun = true;
  ```
- ***Never*** use negation for boolean variable names.
  ```node
  // Bad
  let hasNotLoaded = true;
  // Good
  let hasLoaded = false;
  ```

### Comments
- ***Never*** leave commented out code in a commit.
- Only provide comments where the code isn't strictly self-explanatory.  
  *(So no journal or positional marker comments either)*
- Put a space between the comment and its indicator.  
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
