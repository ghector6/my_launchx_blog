---
title: "Learning Cypress Pt. 4"
date: 2022-04-29
description: 'How to use Cypress Commands'
---


# How to use Cypress Commands ❓

Cypress Commands are custom commands that we can write ourselves to test code, this is convenient cause it makes re-usable ♻️ 
our test code. They become very useful when the code test suit grows, so here we´re going to talk about some of the simpliest, 
for that we´re going to create a command that allows us to do some default values for us. (this way we´re going to have just a 
single line of code that will do the work). 👷

## Creating our first custom Cypress.Commands. 🏗️

We´re going to need some steps for this. 👣

1. Open the cypress/support/commands.js and write the following: 📂

![image](https://user-images.githubusercontent.com/99938141/165990242-0eeb339a-955d-4015-a17e-150bddc132af.png)

this assigns the name "createDefaultTodos" to our command and it´s the name that we´re going to be using in order to call it. 

2. Copy the variables form our test file that used to look like this. 🖨️

![image](https://user-images.githubusercontent.com/99938141/165990437-98922145-166b-4aed-af27-33e9f8d9a957.png)

3. Then we add the ability to create our todos, ( remember that when adding the .type() we´re telling Cypress that literally write that at some spot, that spot is
going to be assigned by the .get() and what we specified inside the (). 📝

![image](https://user-images.githubusercontent.com/99938141/165991078-88d1ff8f-3db1-462c-b713-866ec4b36292.png)

4. Now we can update our test (the second one in the previous chapter) by adding the `cy.createDefaultTodos()` this is basically a function that calls from 
the info that we put in the commands.js 📲 so we are saving code lines by just adding one. right after we assign by the `cy.get(".todo-list li")` where to look for 
our todos inputs and count the number of todos by adding the .should() ending up with something like this. ⤵️

![image](https://user-images.githubusercontent.com/99938141/165993132-921186b5-0f13-47ee-bb02-fb7897efcb50.png)

- Our tests must be passig right by now. Remember you can check more about the syntaxis and the params at : https://docs.cypress.io/api/cypress-api/custom-commands#Usage

## Testing the order in which todos are added. ➕

We are going to check now if the todos are added in order. for this we´re going to need a new it test. Remember to use the `cy.createDefaultTodos()` to add
the ones we create before with the comands.

1. Our code will look like this:

![image](https://user-images.githubusercontent.com/99938141/165994326-313b7c18-451e-40dc-8d42-3af441a98fbd.png)


Lets break it down 🤯

The cy.get() is telling us where to look for the item, which in this case is in list named .todo.list li, the eq() tells us the index of where to look at,
the find() is telling us to look for a label inside that list, and the should() is telling what to look for at the item 1. 
that for every other line of code but the different objects. 

Now we can test if the if the 3 todos have been added in the previous we used `cy.get(".todo-list li").should("have.length", 3)` but lets do it different.

### Using `contains()` to count the items 🔢

If we look at the left bottom corner of our app we will see a text that indicates the amount of items left to do. Let´s look at it with our dev tools 👁️‍🗨️
by this we can map the route to it which is at an span with the name .todo-count. 

![image](https://user-images.githubusercontent.com/99938141/165998262-9185be4b-493a-4c73-ab3e-b21e47ffb363.png)


Now we can target with the get() this spot and analize if it contains 3 elements left. Like this:

![image](https://user-images.githubusercontent.com/99938141/165997275-01c3277c-3d77-4c00-9d94-68033ac08efa.png)

Now our entire test looks like this: 

![image](https://user-images.githubusercontent.com/99938141/165997387-bf740a8f-91d4-4268-b280-837b7528c0fd.png)


## Thing to have in mind: 

 our .todo-count is a <span> with multiple elements nested inside of it. The number is wrapped in a <strong> tag, and the words are wrapped in <span> tags. The cy.contains() method will find the appropriate text even though it may be nested in several different tags.

In the above example, we use both cy.should(), and cy.contains().








