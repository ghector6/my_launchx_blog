---
title: "Learning Cypress Pt.2"
date: 2022-04-26
description: 'Starting Cypress and Writting my first test'
---

# Starting Cypress and Writting our first code. 🚀 

## Starting ▶️

Once you have installed Cypress and edit your script at the package.json we neeed to run the application in a separate terminal window because Cypress needs it 
in order to execute tests ✔️.

Enter the following command to start the app `yarn start` this will make the server work, in another terminal you can open CYPRESS with `yarn cypress:open` that will display
a new browser window with the files from your directory. You can now choose bewtween different browsers.

## Writing our first test 🤓
- We first need to create our file 🗃️.
- We use the function `describe()` to organize our tests. inside the () we put the name  of our block and assign the function: `describe("React todoMVC", () => {})` .
- Within the describe block we will write the name of our tests using `it()` function and assigning it a name that descibes what that test do. 
FI: `it("adds a single todo", () =>{})` so far the statement ends up looking like this:

![image](https://user-images.githubusercontent.com/99938141/165397357-754254fa-aa7a-4f25-ac29-e0e714ca49a2.png)


- To write the test 📄 we first need to know what are we testing and its requirements, in this case we´re addding todos, so we need 
1. Focus on the input field. 
2. Enter the name of our todo.
3. Press enter to add our todo.

### Writing this steps in our test 🧪

- We need to grab the input field from the DOM in order to assign the right elemento to Cypress, for this, using the dev tools from our browser will help. 
- Once we know the element (a class in this case) name we can assign a `cy.get()` to this element, like this : `cy.get(".new-todo") //this targets the class new-todo`
so, our entire test will look like this at this point 🛗  . 

```
describe("React TodoMVC", () => {
  it("adds a single todo", () => {
    cy.get(".new-todo")
  })
}) 
```
- Once Cypress is launched, you will see several files, select our file. With the acxtual code we´re going to have this error 

![image](https://user-images.githubusercontent.com/99938141/165400645-350f2317-699e-4a8b-8963-b3efb2e84de4.png)


This error is telling us that it is unable to get the cy.get() this is because we are not telling Cypress where it can get the info from ❎.

- To tell Cypress where to get the info from, we will need to add `cy.()` , this will look like this:

```
describe("React TodoMVC", () => {
  it("adds a single todo", () => {
    cy.visit("http://localhost8888")
    cy.get(.new-todo")
  })
})
```

- Everytime you save the file Cypress runs. Now we can se that our file is conected 🌐.
- Now we can enter a name of our to todo by using the `cy.type()` adding a string of our choice to type in the input. this looks like this `cy.get(".new-todo).type("Learn Cypress")`
- As it is a end to end it simulates what a user would do so we can add a {enter} like this.  `cy.get(".new-todo).type("Learn Cypress{enter}")`.
this will pass the info to the list: 

![image](https://user-images.githubusercontent.com/99938141/165403008-e7b06b6e-29ee-492a-ac91-ddda8840909b.png)


So far our test file will look like this 🗄️. 
```
describe("React TodoMVC", () => {
  it("adds a single todo", () => {
    cy.visit("http://localhost8888")
    cy.get(.new-todo").type("Learn Cypress{enter}")
  })
})
```

#### Now what ❔

Our test confirms that we can add a single todo but now we need a way to see if it is only going to be one todo. we can do this like this:

1. With the dev tools we need to inspect where is our todo added.
2. Now that we know where it is and the type of element, a li this time, we make an assertion that only one li element exists in our app todo 👓:

```
describe("React TodoMVC", () => {
  it("adds a single todo", () => {
    cy.visit("http://localhost:8888")
    cy.get(".new-todo").type("Learn Cypress{enter}")
    cy.get(".todo-list li").should("have.length", 1)
  })
})
```
- If we add another todo to the test it is goig to break 🖍️.
```
describe("React TodoMVC", () => {
  it("adds a single todo", () => {
    cy.visit("http://localhost:8888")
    cy.get(".new-todo").type("Learn Cypress{enter}")
    cy.get(".new-todo").type("Learn Java{enter}")
    cy.get(".todo-list li").should("have.length", 1)
  })
})
```

- We can simplify this statement like this and change the length in order to make it pass. 🥇
```
describe("React TodoMVC", () => {
  it("adds a single todo", () => {
    cy.visit("http://localhost:8888")
    cy.get(".new-todo").type("Learn Cypress{enter}").type("Learn JavaScript{enter}")
    cy.get(".todo-list li").should("have.length", 2)
  })
})
```


  
  
  
  
  
