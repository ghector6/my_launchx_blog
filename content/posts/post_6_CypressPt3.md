---
title: "Learning Cypress Pt. 3"
date: 2022-04-27
description: 'Setting up Data Before Each Test'
---

# Setting Up Data Before Each Test. 👩‍🔬


## Adding more tests. 📐

- Now that we have crated our new test is time to add another one so we can test if our app can take multiple chores 🏁.
for this we´re going to need another it() function. This time we will add 3 todos.

![image](https://user-images.githubusercontent.com/99938141/165583991-ee360676-7bc9-49cb-b27d-6e7da4526881.png)

- If we are clever we should remember that the first thing we did before was telling Cypress where to take the info from, 
for this we´re going to need again the `cy.visit()`. We´re going to need it for every it() function because everyone is an
independent test. This might look like something annoying, but in fact it has a really nice solution. 🧮

### beforeEach() Solution: 🧐

- Mocha provide us with an elegant solution for the problem above, we use the `beforeEach()` 
function before every test you want to run, getting something that looks like this:

![image](https://user-images.githubusercontent.com/99938141/165585997-37057e0f-0d53-47de-976d-4131883af470.png)

So if you look in detail to the image above you will see that we declare beforeEach function and in the body of that statement we call
our cy.visit() to tell crypress where to look at 👀.

## Writing Multiple Todos. 🖋️

- Now that we have a route, we need to write the new it() and the elements that it is going to test.
For this we´re going to write three new todos like this: 

![image](https://user-images.githubusercontent.com/99938141/165587224-739659a5-496e-4f09-a762-01081b4cb57f.png)

If you notice we´re still using the same elements than before, our Cypress will pass this with no problem. But if you
look closely to the image, you´re going to see that we´re repeating ourselves again. So we need a more practical solution. 📑

- Instead ot typing every and each one of the todo, we can assign them to variables. So we are going to refactor them. like this:


![image](https://user-images.githubusercontent.com/99938141/165589987-516e848a-11d0-4e72-af70-d07b7151b773.png)

look how they are declared right underneath our describe() block, just as we would declare them in JS. If we update
the todos to use the new variables we end up with something like this ⏯️ : 

![image](https://user-images.githubusercontent.com/99938141/165590588-489d614a-5523-4a06-81ce-5ea83ab55ed8.png)

this is going to allow us to reuse our code for multiple tests, now we only need to prove that only three
todos have been added. with the `cy.get(".todo-list li").should("have.length", 3)` libe we can complete our code


## Making our tests more robust 🦾

- So far we have a really useful test but isn´t that specific yet, for this we´re going to add some asserts that allow us
to check if when rendering the text is correct. 🔡
For this we´re going to update our first test, once we have it working we can add it and addapt it to our next test.

We are gonna need our trusty dev tool to inspect 👓 our app, we want to ensure that the text that we write at the input
is exactly the same we get in our todos. As we saw before the li is where our elements are, but we need to go further.
By using the dev tools we can analize that our li contains an < label > which is where our todo name is wrapped. 👣
Knowing this allow us to assert that the todo´s name is in that label element.  So we´re going to need some steps 👟

1. Get all of the < li > elements🤏
    - `cy.get(".todo-list li")`
2. Make sure we grab the first element in this array by using the .eq() method 🥇
    - `cy.get(".todo-list li").eq(0)`
 this will return us the first element in the array.
3. Use the find() method to find the label element. 
    - `cy.get(".todo-list li").eq(0).find("label")`
 Here we get the first li element from the todo-list and then the elemtn that´s inside which must be a label element 📞
4. Finally we use the should() to see if that label contains the text of our todo item: 🔭
    - `cy.get(".todo-list li").eq(0).find("label").should("contain", TODO_ITEM_ONE)`
    
- So it will translate like this: You are going to get from the list items nested in ul named todo-list,  
 the one that is in index 0 which is the first one and find if the TODO_ITEM_ONE Variable is the same one contained. 🥅





