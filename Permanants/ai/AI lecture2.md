---
tags:
  - type/note
  - type/technical
  - theme/ai
aliases: 
lead: Practical guide to AI-assisted coding techniques
visual: 
created: 2024-03-21, 15:22
modified: 2024-03-21, 15:22
template_type: Note
template_version: "1.35"
license: © 2024 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-16T21:53
---

  

# Let's master AI-assisted coding

  

```dataviewjs

dv.paragraph(dv.current().visual);

```

  

<small>_Zoom: [[]] | Edit: [[]]_</small>

  

> [!Summary]

> Comprehensive techniques for leveraging AI in coding, including code generation, testing, documentation, and learning.

  

**Details**

  

<!-- Main content in body of my note  -->

  

## 1. Code Generation Techniques

  

### Using Pseudocode

  

```javascript

/* Example Pseudocode Style 1:

function getBookById(bookArr, id)

    for each book in bookArr

        if book.id === id

            return book

        else return error object "No book found"

*/

  

/* Example Pseudocode Style 2 (Conversational):

Write a function findBookById which:

- Takes bookArr and id as arguments

- Compares each book's id with passed id

- Returns book if found, error if not

*/

```

  

### Using Pseudo Language for Components

  

```

# ComponentTemplate

  

State:

- stateVariable: initialValue

  

Props:

- propName: propType

  

Render:

- Description of render content

  

Event Handlers:

- handlerName: Description of handler functionality

```

  

## 2. Edge Case Generation

  

Key Areas to Consider:

  

- Empty inputs

- Null/undefined values

- Type mismatches

- Boundary conditions

- Performance limits

- Special characters

- Data structure variations

  

Example Template:

  

```javascript

// Test Case Structure

console.log('case description: ', function(edgeCase))

  

// Edge Cases Categories

- Empty/Null inputs

- Type variations

- Boundary values

- Special formats

```

  

## 3. Test Case Generation

  

Structure for Test Cases:

  

1. Basic functionality

2. Edge cases

3. Error conditions

4. Performance scenarios

  

Example:

  

```javascript

// Test Template

// Test Case 1: Basic functionality

let input1 = [normal case];

console.log(function(input1));

  

// Test Case 2: Edge case

let input2 = [edge case];

console.log(function(input2));

  

// Test Case 3: Error condition

let input3 = [error case];

console.log(function(input3));

```

  

## 4. Documentation Generation

  

### JSDoc Format

  

```javascript

/**

 * @description Function description

 * @param {type} paramName - Parameter description

 * @returns {type} Return value description

 * @throws {ErrorType} Error description

 */

```

  

### Style Guide Generation

  

Key areas:

  

- Variable declarations

- Syntax preferences

- Naming conventions

- Code organization

- Comment standards

  

## 5. Learning Techniques

  

1. Topic Exploration

  

   - Request broad overview

   - Drill down into specifics

   - Ask for practical examples

  

2. Resource Gathering

  

   - Request curated articles

   - Ask for learning paths

   - Get practice exercises

  

3. Knowledge Testing

   - Request quizzes

   - Solve practice problems

   - Get feedback on solutions

  

**Supporting Content**

  

<!-- Supporting content in tail of my note  -->

  

- [Scrimba Prompt Engineering Course](https://v2.scrimba.com/prompt-engineering-for-web-developers-c02o/~01)

- [Google Gemini](https://gemini.google.com/app)

- Practice exercises and examples


## Using AI for job search.

  

- Doubt this could be helpful but will take anyway.

  

## Generate, Learn and Practice DS/Algo problems.

  

- Best applicable for intermediate level.

  

---

  

# Back Matter

  

**Source**

  

<!-- Always keep a link to the source- -->

  

- based_on:: Scrimba course and practical experience

  

**References**

  

<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->

  


**Terms**

<!-- Links to definition pages. -->

**Target**


<!-- Link to project note or externaly published content. -->

- used_in:: 

---

**Tasks**
<!-- What remains to be done with this note? -->

- [ ] Add more code generation examples

- [ ] Create section on API documentation

- [ ] Add troubleshooting guide

- [ ] Include more learning resources

**Questions**

<!-- What remains for you to consider? -->

- question:: How to effectively generate complex architectural patterns?

- question:: What are the best practices for generating test cases?

- question:: How to validate AI-generated documentation?

---

**Template Help**

  

<!-- Links to external help pages on GitHub. -->

  

- [Basic Template Structure](https://github.com/groepl/Obsidian-Templates#basic-template-structure)

- [How to Use Links](https://github.com/groepl/Obsidian-Templates#how-to-use-links)

- [How to Use Tags](https://github.com/groepl/Obsidian-Templates#how-to-use-tags)

- [How to Search Notes](https://github.com/groepl/Obsidian-Templates#how-to-search-notes)

- [Plugins Needed](https://github.com/groepl/Obsidian-Templates#obsidian-plugins-needed)

- [Find Latest Updates](https://github.com/groepl/Obsidian-Templates)