---
title: "Learning Cypress Pt.1"
date: 2022-04-26
description: 'What is Cypress and how to install it'
---

# What is Cypress ❓ 

-Cypress is an end to end testing tool for QA engineers and for developers. end to end is a methodology used in SDLC 🤖 to test an application under "real life circumstances".<br> 

-Cypress is independent to Selenium, it works with NodeJs and JS, so we can have better interaction with it.<br>

-The main goal of cypress is to focus on giving the user the best experience by creatin end to end testing meaning it will simulate the way a user 
is going to use our app product🧠.<br>

-Cypress can work with any front-end framework (anything that runs through a web browser basically) such as React, Angular, Vue. But it´s a powerfull tool that also works 
with older server rendered pages or apps 🧰.<br>

-Cypress only works with JavaScript ✍️ .<br>

-One of the best features in Cypress is that when installed it comes with multiple tools in one, so we don´t need to install tons of libraries in order to use it
and they aso come working together properly. 😀<br>

-Another cool feature is how fast it is, it is built in order to make the testing and the development process both simultaneously, making your code better, cleaner and more
efficient.

## Installing Cypress 💻

Cypress can be installed in different ways.<br>
- Via npm by using the `npm install cypress --save-dev` command (you can check the link below to see more options) .
  - You will need node 12 or 14 and above intalled on your computer for this option
- Direct download.

You can look up for the requirement at https://docs.cypress.io/guides/getting-started/installing-cypress#npm-install 

## Opening Cypress 🚪

Be sure to be at your project root and run the `./node_modules/.bin/cypress open` command. Or you can use a shorter code `(npm bin)/cypress open` . <br>
This will launch the the CTR to find a compatible browser.

### Adding npm scripts 👐

It´s better to add the Cypress commands to yout script field in the package.json . <br>
![image](https://user-images.githubusercontent.com/99938141/165379018-a6e9e6ef-bbfd-44b7-b371-fad789ac8946.png)










