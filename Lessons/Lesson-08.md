# FEW 2.4 Navigation Part 2

A second look at navigation with Tab Navigator and Drawer Navigator. We will also look at how to display icons in your app. 

## Learning Objectives/Competencies

- Build the List detail view navigation scheme with React Native

## Tabs and Drawers

Tabbed navigation appears is common on iOS and also appears on Android. Drawer navigation appears on Android and rarely on iOS. On iOS, the tab always appears at the bottom. 

There is a Tabbed starter project option when using `expo init`, I found this project code to be a little more complex than needed. I suspect most people would end up undoing more than they would use with this project. 

- [Drawer Navigator Starter](https://reactnavigation.org/docs/en/drawer-based-navigation.html) (Note! See my notes below tl;dr this did not work for me)

I tested these both on my iOS device.  

### Tab Navigator 

To get started with tabbed navigation you'll need to spin up a react native app along with the required dependancies. 

`expo init tabbed-example`

Install react navigation:

`npm install @react-navigation/native`

Get the expo dependancies:

`expo install react-native-gesture-handler react-native-reanimated react-native-screens react-native-safe-area-context @react-native-community/masked-view`

Get the bottom tabs:

`npm install @react-navigation/bottom-tabs`

One more time in case soemthing was missing:

`npm install`

Test your app with `yarn start`, `npm start`, `yarn ios` or which ever method you prefer. 

If everything is working create some tabbed navigation. 

Copy yhe sample code here: 

https://reactnavigation.org/docs/tab-based-navigation/

This creates a bare bones application with two tabs. 

**Challenge:**

- Add another tab to the tab bar. Follow these steps: 
  - Make a new component screen. This can be a function that returns a `<View>` with some `<Text>`
  - Add a new `<Tab.Screen>` as a child of `<Tab.Navigator>`. You can put this below the existing tab screens. Assign it your new component. 

## Icons 

Icons appear on mobile in many places. If you can make them flexible in size that's even better. There are several libraries that make icons these notes will cover [react-native-vector-icons](https://github.com/oblador/react-native-vector-icons).

This library has several sets of bundled icons. Start by importing the library. 

`npm install --save react-native-vector-icons`

I had to link my icons using, this may not be needed for everyone: 

`npx react-native link`

`npx react-native link react-native-vector-icons`

In your React Native project import the icon with: 

`import { Ionicons } from 'react-native-vector-icons'`

Use the icon with: 

`<Ionicons name="ios-add-circle-outline" size={32} />`

This should display a 32pt icon that looks like a circle with a plus in the center.

You can put this component almost anywhere! Seems like these need to be wrapped in a `<Text></Text>` component. 

**Note!** Finding the name to use for a specific icon is not as easy as you might think. The names shown with the icon bundles are not always what you need to set as the name in the component!

If you get a warning that the name isn't working for an icon open the warning and read the names! It will list all of the names that are possible values. 

**Activity:** Add some icons to the Home and Settings Screens. 

**Challenges:**

- Make an icon that appears on the Home Screen
- Make an icon that appears on the Settings Screen 
- Set the and color of the icons

Explore Icons here: 

Look at the bundled icon sets: https://github.com/oblador/react-native-vector-icons#bundled-icon-sets.

**Challenges:** 

- Make some icons in a Screen. You'll need to: 
	- Import the icon set you want to use
	- Figure out the name of the icon you want to see (this might take some experimentation)
	- Add and configure an Icon component in your Screen
	
**Stretch Challenge:**

- Make an Icon button. 
	- Follow the guide [here](https://github.com/oblador/react-native-vector-icons#iconbutton-component)

## Tab Bar Icons 

The docs show a solution in the [customizing the appearance](https://reactnavigation.org/docs/tab-based-navigation/#customizing-the-appearance) section of the React Navigation Tab Bar Example. This example looks a little complex as it uses the React-Native-Vector-Icons and includes a badge on the icon.

Notice that big block of code inside:

`<Tab.Navigator screenOptions={...lots of code here...} >`

This function returns an object thqt includes a property: `tabBarIcon`. This property is a function that receives an object with three properties: `focused, color, size`. You'll use these values to generate an icon and return it. 

The sample code 

**Challenge:**

Add a custom icon for your new tab bar view. Find an icon you like. In the `tabBarIcon` function add a new else if block. This case should look for `route.name` to identify the icon. Look up an icon in the icon set. 

Note: Many icons have a solid and outline version. You can use the solid for the focussed state and the outline when the tab is not focussed. 

```JS
if (route.name === 'Home') {
  iconName = focused ? 'ios-information-circle' : 'ios-information-circle-outline';
} else if (route.name === 'Settings') {
  iconName = focused ? 'ios-list-box' : 'ios-list';
} else if (route.name === 'Other') {
  iconName = focused ? 'ios-star' : 'ios-star-outline';
}
```

Here I used the icons 'ios-star' and 'ios-star-outline' for the icon used in the 'Other' route. 

### Tab Navigator Recap

Discussion: 

- Quickly describe how tabnavigator is constructed
- How are icons added? 
- What other options can be applied? 

Stretch challenges: 

- Add a stack navigator to one of the tabs screens

### Drawer Navigator

I had a hard time getting this to work. I suspect this was because I was working on iOS. 

The default sample code [here](https://reactnavigation.org/docs/en/drawer-based-navigation.html) did NOT work for me on iOS. 

What DID work for me was this example: 

- https://snack.expo.io/@aboutreact/navigationdrawer-example?session_id=snack-session-5vdX_nqe_

To get this working I did the following: 

- Download the sample code. This was incomplete and possible not using the latest version of React Native and React Navigator. 
- Make a new blank project with `expo init`. 
- Copy the following files from [example](https://snack.expo.io/@aboutreact/navigationdrawer-example?session_id=snack-session-5vdX_nqe_) and paste them into a new project you created in the previous step. 
    - App.js
    - app.json
    - assets
    - image
    - pages
    
The package.json from the example code is missing a few things. Don't copy this! You will need to add react-navigation

`npm install react-navigation`

This worked for me and generated a simple app with a drawer and three subpages. 

Please let me know if missed a step here. It was hard to backtrack over my experiments and note them here. 

## Apply navigation concepts

Apply the navigation concepts from class to your final project. Choose a navigation scheme for your project and create a minimal implementation to get started. Mockup any Screens you may need with a Text label naming the content that will eventually be there. 

Do this now in class! 

## After Class

- Continue working on the final project. Focus on building navigation and passing data to screens. 

## Additional Resources

- React Navigation
	- Tabs
		- https://reactnavigation.org/docs/en/tab-based-navigation.html
		- https://reactnavigation.org/docs/en/tab-based-navigation.html#minimal-example-of-tab-based-navigation
		- https://reactnavigation.org/docs/en/tab-based-navigation.html#customizing-the-appearance
		- https://reactnavigation.org/docs/en/bottom-tab-navigator.html#bottomtabnavigatorconfig
	- Vector Icons 
		- https://github.com/oblador/react-native-vector-icons
		- https://github.com/oblador/react-native-vector-icons#iconbutton-component
	- Drawers 
		- https://reactnavigation.org/docs/en/drawer-based-navigation.html
		- https://snack.expo.io/@aboutreact/navigationdrawer-example?session_id=snack-session-5vdX_nqe_

