## Setting up Cypress in WSL
* Follow this link for a detailed guide: https://nickymeuleman.netlify.app/blog/gui-on-wsl2-cypress

## Good Practices
* Favor writing longer tests. Tests do not maintain state between them, so writing longer tests will reduce the time it takes to reload everything into state and re-authenticate between tests. A good length to shoot for is testing an entire page or an entire flow in a single test. This will also reduce the cost of running too many tests in Cypress Dashboard.
* Implementing test variables is a great way to get specific elements.
  * data-cy example: `<td className="budget-table--number" key={q} data-cy="subtotal">`
* Working with variables based on the DOM can be tricky. Here's a few pointers from what I've learned:
  * You can only work with one type of element at a time. If you need to interact with a `budget-table--number` you can then _only_ interact with those elements. Trying to access any other element results in a infinite loop. 
  * Here's the syntax for interacting with elements in the DOM:
    * `cy.get({ELEMENT}).should($elem => {do whatever with $elem})`
      * .should() can be replaced with .then()
      * .eq(num) can be used to index through multiple $elems
      * You cannot get the values of $elem outside of the .should(). If you try to store the value into a variable declared outside of the .should() it will not save. Meaning all of the work that depends on these elements _must_ be done within the .should()
      * Since you can only interact with one specific type of element, test variables are a good way to select elements that have different class names.
* Cypress documentation is very well written. Here is all the commands: https://docs.cypress.io/api/table-of-contents
* Cypress testing library commands: https://testing-library.com/docs/guiding-principles/
* You can control the order in which the tests execute by adding a number in the beginning of the test file name.
* Page objects should be used to access specific elements on a page; instead of using a long string of selectors in a spec file (which hinders readability and may result in repetitive and brittle code if the page layout changes), place the selectors as a method in a page object. e.g. instead of `cy.get({ELEMENT}).find({SUBELEMENT})`, a method `page.get_subelement() = cy.get({ELEMENT}).find({SUBELEMENT})` should be used instead.
* For finding text, case-insensitive regex commands are preferred to lower the chance of minor punctuation changes breaking tests.
     
## Useful Commands
* .next(), .parent(), and .prev() are good ways to get to an element you might be having trouble accessing.
* .contains() and .findAllByText() are different and each have their respective uses.
  * .contains() simply finds if whatever is passed exists. While .findAllByText() looks for exactly what was passed.
    * Example: "Other Funding Subtotal". cy.contains("Other Funding") return true, cy.findAllByText("Other Funding") return false.
  * You can use a regex search in .findAllByText() and it will find elements based on partial matches and you can search for case-insensitive matches.
    * Example: "Other Funding Subtotal". cy.findAllByText(/Other Funding/) returns true and cy.findAllByText(/Other funding/i) returns true.
* .within() is good for when you want to focus on one element, for example checking a table. 
* .invoke('text') yields the text of a selected element and can be used to work with the text.
* .eq(N) yields the (N+1)th member of a list of selected items. e.g. `cy.get('li').eq(3)` will get the 4th list item in the DOM.
## Storing/Working with Data Constants
* Cypress data constants can be held within a json in the fixtures folder. 
* They are easy to access, you just need to load the fixture in before each test you use them in.
  * syntax: `cy.fixture('activity-overview-template.json').as('data');`
* Also worth noting that arrow functions do not work with fixtures, you need to use the traditional function() syntax.
## Where to store helper functions
* Pages are a good way to store helper functions. They work like normal helper function but you have to include the page in the header of the file. 