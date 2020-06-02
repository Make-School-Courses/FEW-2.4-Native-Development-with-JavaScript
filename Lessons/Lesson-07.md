# FEW 2.4 React Navigation

**Switch this over to React Native Router**

https://medium.com/osedea/react-native-navigation-solutions-in-2018-6ff1dd7f6d20

This goal of this leasson is to introduce navigation concepts on mobile and apply them. 

## Learning Objectives/Competencies

- Identify navigation paradigms on mobile
	- Stack
	- Tab
	- Drawer
	- Modal
- Implement and build stack navigator
	- Manage a navigation stack
- Use static properties and methods

## Navigation on Native

On mobile devices space is at a premium and primary content is text which runs horizontally while we are usually viewing in portrait. 

The nature of this environment is such that design dictates that we usually want to make content fill the space and minimize the number of items displayed. 

Rather than showing mulitple content elements simultaneously we opt to focus on a single item. To fit all of your content into a mobile application you're either scrolling or navigating between views. 

Each new whole page of stuff is a screen. Really it's a view with many child views. In iOS native development it's called a ViewController. In React we call it a Component. 

For this dicussion let's use the name **Screen** when we are talking about a view that contains the entire current screen of content and use the term Component or View when we are talking about a sub view. 

## Navigating Screens

On the web we navigate between pages and the browser keeps track of navigation in the history. On mobile we don't have this convenience as a default behavior. 

Generally speaking on mobile your apps will use one of four navigation schemes:

- Stacks
- Tabs
- Drawers
- Modals

Your app might use any combination of these at the same time. 

A **Stack** is a series of Screens. This is similar to what you see in the browser. There is a history. You can push and pop Screens on a stack the same way you can push and pop elements in an array. When you see the back button in a mobile app you're using a stack. 

**Tabs** appear at the bottom of the screen and manage a fixed set of Screens. The tabs appear on top of all Screens! Any Screen in tabbed navigation might be a Stack! 

**Drawers** act like tabs but the drawer is hidden until displayed, usually by tapping the "Hamburger" menu. Like Tabs, Drawers are available from any Screen, and anything they display might be a Stack. 

**Modal** Views appear above the current Screen. Imagine a modal as out side of a stack. Anytime you close/dismiss a modal view you are returned to previous Screen. Really you never left, the modal view just appeared on top to ask a clarifying question then went away.

![Navigation Illustration](./images/lesson-07.png)

## Navigator

A Navigator is the parent for any set of screens. A navigator is usually a Stack, Tab, or Drawer. Any of the screens displayed might be a Stack. 

## Navigation Libraries for native

- [React Navigation](https://reactnavigation.org/)
- [React Native Router Flux](https://github.com/aksonov/react-native-router-flux)
- [React Router Native](https://github.com/ReactTraining/react-router/tree/master/packages/react-router-native)

I chose [React Navigation](https://reactnavigation.org/) for these examples since it has all of the features any project might need, works on Android and iOS, and was recommended by React Native. This is an open source solution. 

## React Native Navigation

React Navigation is a library for React Native that is open source. It provides all of the basic native navigation systems and works on Android and iOS. 

- https://reactnavigation.org/docs/en/getting-started.html
- https://facebook.github.io/react-native/docs/navigation

**Get started by importing the library**

- `npm install --save react-navigation`

**Creating a Stack View** 

Create a root component that will act as the main navigator. This can be the App component. If you're using a single Stack it should be App. 

```JS
import { createStackNavigator, createAppContainer } from 'react-navigation'
import HomeScreen from './HomeScreen'
import DetailScreen from './DetailScreen'

const MainNavigator = createStackNavigator({
  Home: { screen: HomeScreen },
  Detail: { screen: DetailScreen }
})

const App = createAppContainer(MainNavigator)

export default App
```
The example above creates a main navigator that displays one of two components: HomeScreen, and DetailScreen. Before this will work you need to create both of these components. 

- Create HomeScreen. 
- Create DetailScreen.

Use a class component for these. While you can use a stateless component it becomes difficult to access `navigationOptions`. Using a class based components avoids this. 

With these created running the project should create a navigator component that displays HomeScreen. 

### Navigating to another screen

Screens defined in a stack navigator component, HomeScreen and DetailScreen in this example receive a `navigation` object in props. This object has properties and methods that facilitate navigation. 

To navigate to another screen call: 

```JS
navigation.navigate('Detail')
```

or 

```JS
props.navigation.navigate('Home')
```

### Navigation Bar

The navigation bar is a standard UI element. It displays a title in the center and buttons on the left and the right. 

Setting the title will cause the navigation bar to display. Do this by setting some navigation options on a `static` property of your HomeScreen. 

```JS
class HomeScreen extends Component {
	...
	static navigationOptions = {
		title: 'Navigation Example'
	}
	...
}
```

This `static navigationOptions` should appear inside the class body, and not in a method or the constructor. 

**Note!** Static properties are properties that are accessed through the class instead of through an instance of a class. You can think of static properties as shared by all instances of a class, where each instance of a class stores it's own values for properties assigned to `this`.

Here state is used to share navigationOptions with all screens in a stack navigator. 

Add a title to HomeScreen and DetailScreen. 

## Passing Data to a Screen

When navigating to a screen you will sometimes want to pass some data that screen will display. This allows you to reuse a screen, for example a user profile screen could display any user profile. 

**Sending params to a Screen**

To pass data to a screen follow these steps. 

- Organize data in an object. 
- Pass the object as the second parameter of navigation.navigate(Screen, DataObject). 

For example: 

HomeScreen.js

```JS
...
this.props.navigation.navigate('Detail', { message: 'Hello!' })
...
```

**Receiving Data in a Screen**

Props are passed as an object with values assigned to properties. You can get at these properties individually by key with `getParams()` or get the entire object. 

Gets named prop and supplies default value if missing.

`props.navigation.getParam('message', 'world') // 'Hello!'` 

or gets the entire params object

`props.navigation.state.params // { message: 'Hello!' }`

DetailScreen.js

```js
...
const { navigation } = this.props
const message = navigation.getParam('message', 'default value')
...
```

## Table View Detail View 

On iOS the TableView is the equivalent of the FlatList in React Native. Tapping a list cell to display a another view with information realted to selected cell is a very common navigation pattern.

The class example will take a secon look at the By Breed app from a previous class. This time we will display a list of breed names in a FlatList, tapping a breed will display information about the breed in a detail screen. 

[**Download the starter project**](https://github.com/soggybag/navigation-list-starter)

Follow the instructions in the Readme for the project. 

## Plan your navigation

Look at your final project. Ask yourself what type of navigation it will use? Diagram this in any way you like. Identify navigation systems used. 

- Stack Navigator
- Tabbed Navigation 
- Drawer Navigation
- Modal Views

Start working on your project. Start by building your navigation system. Mock up the Content Screens with a a view and text to test your navigation. 

## After Class

- 

## Additional Resources

- 


