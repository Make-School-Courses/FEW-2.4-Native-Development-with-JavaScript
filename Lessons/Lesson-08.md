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

This was easy to get working. I started by copy and paste the code here: 

- [Tabbed Navigator starter](https://reactnavigation.org/docs/en/tab-based-navigation.html)

This worked right off. I pasted everything into App.js. You could build off this to get started with a new app. 

I also tested the default **Tabbed Application** option when running `expo init`, this is the second option "Tabs". While this project worked it had a lot of extra files and things that I would imagine myself having to undo to make my own app. This seemed like more work, your mileage may vary. 

## Build a Tab bar application!

In this section, you will build your own tabbed application to test the tabbed navigator. 

### Getting started

Start a new React Native application. Be sure to choose **blank** app as the starter. We will write the code to make the tab navigator ourselves. 

`expo init tabbed-app`

Navigate into this folder:

`cd tabbed-app`

We will use React Navigation for this

`npm install --save react-navigation`

Install dependencies 

`npm install`

Run the app to make sure everything is working: 

`yarn start`

### Minimal Tabbed Application

Paste the code snippet from the [minimal example of tab-based navigation](https://reactnavigation.org/docs/en/tab-based-navigation.html#minimal-example-of-tab-based-navigation) into App.js. 

I reproduced it here for convenience: 

```JSX
import React from 'react';
import { Text, View } from 'react-native';
import { createBottomTabNavigator, createAppContainer } from 'react-navigation';

class HomeScreen extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
        <Text>Home!</Text>
      </View>
    );
  }
}

class SettingsScreen extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
        <Text>Settings!</Text>
      </View>
    );
  }
}

const TabNavigator = createBottomTabNavigator({
  Home: HomeScreen,
  Settings: SettingsScreen,
});

export default createAppContainer(TabNavigator);
```

Quick discussion: 

- What is happening here? 
- Can we improve on this code block?

## Icons 

Icons appear on mobile in many places. If you can make them flexible in size that's even better.  There are several libraries that make icons these notes will cover [react-native-vector-icons](https://github.com/oblador/react-native-vector-icons).

This library has several sets of bundled icons. Start by importing the library. 

`npm install --save react-native-vector-icons`

In your React Native project import the icon with: 

`import { Ionicons } from 'react-native-vector-icons'`

Use the icon with: 

`<Ionicons name="ios-add-circle-outline" size={32} />`

This should display a 32pt icon that looks like a circle with a plus in the center.

**Note!** Finding the name to use for a specific icon is not as easy as you might think. The names shown with the icon bundles are not always what you need to set as the name in the component!

If you get a warning that the name isn't working for an icon open the warning and read the names! It will list all of the names that are possible values. 

Activity: Add some icons to the Home and Settings Screens. 

Challenges: 

- Make an icon that appears on the Home Screen
- Make an icon that appears on the Settings Screen 
- Set the and color of the icons

Explore Icons here: 

Look at the bundled icon sets: https://github.com/oblador/react-native-vector-icons#bundled-icon-sets

## Tab Bar Icons 

The docs show a solution in the [customizing the appearance](https://reactnavigation.org/docs/en/tab-based-navigation.html#customizing-the-appearance) section of the React Navigation Tab Bar Example. This example looks a little complex as it uses the React-Native-Vector-Icons and includes a badge on the icon.

Set the tab icons by 

`createBottomTabNavigator(RouteConfigs, BottomTabNavigatorConfig)`

The first parameter defines the routes/Screens the tab navigator will display. The second parameter defines options for the tab navigator which includes defining the icons to display and the colors. 

[BottomTabNavigatorConfig](https://reactnavigation.org/docs/en/bottom-tab-navigator.html#bottomtabnavigatorconfig) read option here. This doesn't explain a whole lot but the example code provides some insights. You can use the following snippet to generate icons for the Simple Tab bar example: 

```JS
{
    defaultNavigationOptions: ({ navigation}) => ({
        tabBarIcon: ({ focused, horizontal, tintColor }) => {
            const { routeName } = navigation.state
            let iconName 
            switch(routeName) {
                case 'Home': 
                    iconName = 'ios-home'
                    break
                case 'Settings': 
                    iconName = 'ios-settings'
            }
            return <Ionicons name={iconName} size={25} color={tintColor} />
        }
    })
}
```

Discussion: 

- What is going on here? 
- How can we customize this? 

**More Options**

There are a lot more options. One option that you may want to work with is tint and background colors for the active and inactive states. 

You can add this to the BottomTabNavigatorConfig object. 

```JS
tabBarOptions: {
    activeTintColor: 'tomato',
    inactiveTintColor: 'gray',
    activeBackgroundColor: 'gray',
    inactiveBackgroundColor: 'black'
}
```

I used keyword colors, you can use RGB or other color values. Yes, tomato is a color, try rebecapurple, aliceblue, blanchedalmond. On second thought don't, make up your own colors instead! 

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

- https://reactnavigation.org/docs/en/drawer-based-navigation.html
- https://reactnavigation.org/docs/en/tab-based-navigation.html
- https://reactnavigation.org/docs/en/tab-based-navigation.html#minimal-example-of-tab-based-navigation
- https://github.com/oblador/react-native-vector-icons
- https://reactnavigation.org/docs/en/tab-based-navigation.html#customizing-the-appearance
- https://reactnavigation.org/docs/en/bottom-tab-navigator.html#bottomtabnavigatorconfig
- https://reactnavigation.org/docs/en/drawer-based-navigation.html
- https://reactnavigation.org/docs/en/tab-based-navigation.html
- https://snack.expo.io/@aboutreact/navigationdrawer-example?session_id=snack-session-5vdX_nqe_

