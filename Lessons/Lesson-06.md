# FEW 2.4 Class 8 Defining a project

From here until the end of the term you will be working on your final project. Your goal is to define what the project is and plan how you will complete it between now and the end of the term. 

## Learning Objectives

- Define project goals
- Identify the platform
- Map out milestones

## React Native Q and A

What kinds of questions do you have so far about React Native? 
	
- Native Components in general
- Specific Components
	- FlatList 
	- View 
	- Text 

## Defining the final 

What are you going to make? 

What platform will it use? 

- Mobile
- Desktop

Define milestones for the project. A milestone is a a step in the construction of your project and should have a deliverable.

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

## After Class

- Continue working on your current tutorial
- Complete reading
- Complete challenges

## Additional Resources

- [Controlled Component pattern](https://reactjs.org/docs/forms.html) 
- [InputAccessoryView]( https://facebook.github.io/react-native/docs/inputaccessoryview) - Customizes keyboard input view
- [Picker](https://facebook.github.io/react-native/docs/picker) - Handles multi-choice input with a scrolling list of choices. Good for many choices.
- [PickerIOS](https://facebook.github.io/react-native/docs/pickerios) - iOS Picker View
- [SegmentedConreolIOS](https://facebook.github.io/react-native/docs/segmentedcontrolios) - Multi-choice input, iOS only, good for a few choices. 
- [Slider](https://facebook.github.io/react-native/docs/slider)
- [Switch](https://facebook.github.io/react-native/docs/switch) - Like a checkbox
- [TextInput](https://facebook.github.io/react-native/docs/textinput) - Use for Single line and multi-line text input 