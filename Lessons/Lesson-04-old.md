# FEW 2.4 Class 4 - Electron Lab

Debugging Electron. 

Communication between the Main Process and rendering Processes. 

## Learning Objectives

1. Dog Fooding...
1. Identify problems 
1. Create solutions
1. Use CSS to create user interfaces 
1. Implement communication between main and rendering processes

## What is Dog Fooding? 

https://en.wikipedia.org/wiki/Eating_your_own_dog_food

In a nutshell it's using the product you create! How many times have you done this? If the answer is less than the number of products you have created you're missing a big opportunity to improve those products! 

The goal: Now that you have created your desktop app you should use it. 

If you created the password generator save some passwords. Every time you create a password save it to the app. You can mock this up if you don't want to save real passwords (security). Open it and retreive passwords when you need them. 

If you made the timers app use it to track the time you spend working on homework, studying, reading, working out, and other activities. 

If you made tetris play the game when you're bored. 

The goal is to identify areas where the app could be improved through real world use! You will use your own work and evaluate it. 

Take notes and make changes to the work. Keep a list of all of these changes. 

## Initial Exercise

- CSS and UI issues
	- forms elements
- Electron Options 
	- Size of Window
	- Saving data

## Main Process vs Rendering Process

- What is the main process? 
- What is the rendering process? 
- Creating communication between the two

## Review CSS Grid and Flexbox

Use Grid for two dimensional layouts and Flexbox for arranging things on a single axis. 

Both are applied to a parent container and affect the children. 

You can use Flex box inside a grid or one grid within another grid. 

- Use Grid for two dimensional layouts.
- Use `grid-template-area` for arbitrary layouts use `grid-template-columns` for dynamic content. 

- Use Flexbox for one dimensional layout
- Use think in terms of main axis and cross axis

## After Class

- Wrap up the Electron project. You should have a functional Electron application that runs on the desktop. 
- 

## Additional Resources

- [Electron Passing Data Demo](https://github.com/soggybag/electron-passing-data-demo)
- [ipcRenderer](https://electronjs.org/docs/api/ipc-renderer)
- [ipcMain](https://electronjs.org/docs/api/ipc-main)
