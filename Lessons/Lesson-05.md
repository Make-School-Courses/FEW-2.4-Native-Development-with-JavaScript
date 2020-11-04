# FEW 2.4 Class 5 Defining a project

From here until the end of the term you will be working on your final project. Your goal is to define what the project is and plan how you will complete it between now and the end of the term. 

## Learning Objectives

- Apply Styles to components 
- Explore Native Components and read documentation apply what you find
- Define project goals
- Identify the platform
- Map out milestones

## Styling Components

Components in React Native are styled using inline styles. 

```JavaScript
...
return <View style={{width: 100}}>...</View>
...
```

Use `StyleSheet.create()` for some reason not clearly explained in the docs. The `StyleSheet` also has some helper functions. 

```JavaScript
...
return <View style={styles.container}></View>
...
import { StyleSheet }
const styles = StyleSheet.create({
	container: {
		width: 100
	}
})
```

**Important!** React Native uses CSS styles but there are a few differences between React Native and the Web. 

- Does not support all styles 
- Not all components support all styles 
- All units are pixels/points (with a few expections)

### Flex Box

Everything is styled with Flex. The following properties will take your layouts far. 

- flex
- justifyContent
- alignItems 

Keep in mind that Flexbox applies to children. While Flexbox applies toa . single axis you can mix axis by nesting elements in in a view. 

## React Native Q and A

What kinds of questions do you have so far about React Native? 

## Handling Input 

Touch screen devices have their own input paradigms. Touch screen interaction is a very different experience from mouse driven interaction. 

Discuss the differences

https://facebook.github.io/react-native/docs/handling-touches

React Native provides a few interactive components. 

- Button - Good for basic button
- Touchables - Good when the button isn't enough or can't be styled to meet your needs. 
	- TouchableHighlight
	- TouchableNativeFeedback
	- TouchableOpacity
	- TouchableWithoutNativeFeedback
- TextInput

Use the 'Touchable' components to create custom buttons and things you can tap to handle input. 

## Forms 

Forms on native follow the same patterns used with React on the web with a few unique issues. 

Keyboard avoiding!

Mobile screens are small and space is limited. On mobile the keyboard will often obscure an input field. React Native solves this with it's: 

[KeyboardAvoidingView](https://facebook.github.io/react-native/docs/keyboardavoidingview)

For Text input use: 

- [InputAccessoryView]( https://facebook.github.io/react-native/docs/inputaccessoryview) - Customizes keyboard input view
- [Picker](https://facebook.github.io/react-native/docs/picker) - Handles multi-choice input with a scrolling list of choices. Good for many choices.
- [PickerIOS](https://facebook.github.io/react-native/docs/pickerios) - iOS Picker View
- [SegmentedConreolIOS](https://facebook.github.io/react-native/docs/segmentedcontrolios) - Multi-choice input, iOS only, good for a few choices. 
- [Slider](https://facebook.github.io/react-native/docs/slider)
- [Switch](https://facebook.github.io/react-native/docs/switch) - Like a checkbox
- [TextInput](https://facebook.github.io/react-native/docs/textinput) - Use for Single line and multi-line text input 

## Controlled Component Pattern

Use the [Controlled Component pattern](https://reactjs.org/docs/forms.html) with form elements. 

**tl;dr** Store the value of the input element on state, set the state when the element changes, and set the value of the element from state. 

- Define a property on state
- Set the valuse of the form element it value on state
- Set state when the form element changes

## Activity 

Use components to solve these problems. 

- ScrollView 
	- Make a scrolling view with content Use any components to fill the view.
- FlatList
	- Use header, footer, and or separator in the list
	- Use TextInput to filter list 
- TextInput 
	- Input zip code in Wthr app to show whether
	- Use KeyBoardAvoidingView

## After Class

Define your final project. This must be a native app of some kind. 

## Defining the final 

What are you going to make? 

What platform will it use? 

- Mobile
- Desktop

Define milestones for the project. A milestone is a a step in the construction of your project and should have a deliverable.

## Additional Resources

- [Controlled Component pattern](https://reactjs.org/docs/forms.html) 
- [InputAccessoryView]( https://facebook.github.io/react-native/docs/inputaccessoryview) - Customizes keyboard input view
- [Picker](https://facebook.github.io/react-native/docs/picker) - Handles multi-choice input with a scrolling list of choices. Good for many choices.
- [PickerIOS](https://facebook.github.io/react-native/docs/pickerios) - iOS Picker View
- [SegmentedConreolIOS](https://facebook.github.io/react-native/docs/segmentedcontrolios) - Multi-choice input, iOS only, good for a few choices. 
- [Slider](https://facebook.github.io/react-native/docs/slider)
- [Switch](https://facebook.github.io/react-native/docs/switch) - Like a checkbox
- [TextInput](https://facebook.github.io/react-native/docs/textinput) - Use for Single line and multi-line text input 