# FEW 2.4 Navigation Part 2

A second look at navigation with FlatList and Passing Params. 

## Learning Objectives/Competencies

- Build the List detail view navigation scheme with React Native

## Table View Detail View 

On iOS the TableView is the equivalent of the FlatList in React Native. Tapping a list cell to display a another view with information realted to selected cell is a very common navigation pattern.

The class example will take a secon look at the By Breed app from a previous class. This time we will display a list of breed names in a FlatList, tapping a breed will display information about the breed in a detail screen. 

[**Download the starter project**](https://github.com/soggybag/navigation-list-starter)

Follow the instructions in the Readme for the project. 

## Tabs and Drawers

Tabbed navigation appears is common on iOS and also appears on Android. Drawer navigation appears on Android and rarely on iOS. On iOS the tab always appears at the bottom. 

There is a Tabbed starter project option when using `expo init`, I found this project code to be a little more complex than needed. I suspect most people would end up undoing more than they would use with this project. 

I would recommend starting from the sample code provided here. 

- [Tabbed Navigator starter](https://reactnavigation.org/docs/en/tab-based-navigation.html)
- [Drawer Navigator Starter](https://reactnavigation.org/docs/en/drawer-based-navigation.html) (Note! See my notes below tl;dr this did not work for me)

I tested the TabNavigator and DrawerNavigator on my iOS device. These were my experiences. 

### Tab Navigator 

This was easy to get working. I started by copy and pasting the code here: 

- https://reactnavigation.org/docs/en/tab-based-navigation.html

This worked right off. I pasted everything into App.js. You could build off this pretty easily. 

I also tested the default Tab Navigator from the Tabbed Application option when running `expo init`, this is the second option "Tabs". While this project worked it had a lot of extra files and things that I would imagine myself having undo to make a new app. 

### Drawer Navigator

I had a hard time getting this to work. I suspec this was because I was working on iOS. 

The default sample code [here](https://reactnavigation.org/docs/en/drawer-based-navigation.html) did NOT work for me on iOS. 

What DID work for me was this example: 

- https://snack.expo.io/@aboutreact/navigationdrawer-example?session_id=snack-session-5vdX_nqe_

To get this working I did the following: 

- Download the sample code. This was incomplete and possible not using the latest version of React Native and React Navigator. 
- Make a new blank project with `expo init`. 
- Copy the following files from [example](https://snack.expo.io/@aboutreact/navigationdrawer-example?session_id=snack-session-5vdX_nqe_) and paste them into new project you created in the previous step. 
	- App.js
	- app.json
	- assets
	- image
	- pages
	
The package.json from the example code is missing a few things. Don't copy this! You will need to add react-navigation

`npm install react-navigation`

This worked for me and generated a simple add with a drawer and three sub pages. 

Please let me know if missed a step here. It was hard to backtrack over my experiments and note them here. 

## Apply navigation concepts

Apply the navigation concepts from class to your final project. Choose a navigation scheme for your project and create a minimal implementation to get started. Mock up any Screens you may need with a Text label naming the content that will eventually be there. 

Do this now in class! 

## After Class

- Continue working on final project. Focus on building navigation and passing data to screens. 

## Additional Resources

- https://snack.expo.io/@aboutreact/navigationdrawer-example?session_id=snack-session-5vdX_nqe_
- https://reactnavigation.org/docs/en/tab-based-navigation.html
- https://github.com/soggybag/navigation-list-starter
- 
