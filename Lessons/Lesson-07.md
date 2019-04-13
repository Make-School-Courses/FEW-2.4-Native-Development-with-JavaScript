# FEW 2.4 class 7 - Native Components Part 1

Mobile is the land of small screens in portrait orientation. This is a different environment from the desktop. Building mobile apps require developers to think different to work with the limited space. 

## Learning Objectives

- Display data on mobile
- Differentiate list view and scrollview and their use cases
- Use a FlatList

## ScrollView vs ListView 

Mobile screens are small you'll always be scrollings. There are two ways to handle scrolling. 

- Scrolling a **small** amount of content
- Scrolling a **large** amount of content

**tl;dr** For a small amount of content use a ScrollView. For a large amount of content use a ListView. This is obviously an oversimplified solution.

ScrollView scrolls all of the things. The things exist, they take up more space than fits on the screen, the scrollview scrolls them. Yeah that's what you expected. 

Why is there a ListView and why would you use one?

The ListView manages a large amount of data. Remember when Steve Jobs said you could have 10,000 songs in your pocket? You though it was great. There was a developer somewhere that needed to solve the problem of how to scroll through a list of 10,000 items! 

Seriously imagine creating 10,000 views and loading them in RAM. Sounds like a memory problem. Heck! imagine rendering the pixels that made up a list of table cells where each cell is 40 pixels tall...

That's a 40,000 pixel tall images! If each cell were 320 pixels wide: 

`40 * 320 * 10,000 = 128,000,000`

By comparison the iPhone SE screen is 320 x 568, thats:

`320 * 568 = 181,760`

So with 10,000 table cells listing all of your favorite songs on your iPhone SE you'd need more than 704 screens!

`128,000,000 / 181,760 = 704.2253521127`

What does the ListView do differently? 

The ListView generates enough views to fill the screen. It displays only a subset of data at any moment. As each row view scrolls off the screen it is recycled and populated with new data. 

## Implement ScrollView

- Create a scrollView 
- add some content 
- scroll! 

## Implement FlatList

- Define data 
- Create a FlatList 
- Define props 
	- renderItem
	- keyExtractor
	
Why data? 

FlatList needs to know how many rows you have to work with. Only a subset of the data will be displayed in the list. FlatList keeps track of the starting and ending indexs that are currently displayed. 
	
Why renderItems?

This function returns takes an object with the data and returns a React Native Component that displays as the list cell. FlatList will ask us for the cells it needs, we supply the cell from the data and index. 

The Object passed to renderItems includes three keys: 

- item : The data item for this row
- index : the index of this row in data
- separators : An object with properties that can be used to render separators between rows

Why keyExtractor? 

Each cell needs a unique id, keyExtractor is a method that generates a unique id for each row. You supply a function that takes two prarameters: 

- item : The data item for this row
- index : The index of the row in data

Use this function to generate unique row ids. 





















## Learning Objectives/Competencies

- Use List View 
- Use Scroll View 
- Differentiate the differences and use cases for List and Scroll views 
- Input views and Controlled component pattern
- Handle user input on mobile/touch screen 

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

- 

## Additional Resources

- Compare Android and iOS
	- https://medium.com/@chunchuanlin/android-vs-ios-compare-20-ui-components-patterns-part-1-ad33c2418b45
	- https://medium.com/@vedantha/interaction-design-patterns-ios-vs-android-111055f8a9b7
	- https://www.ready4s.com/blog/android-vs-ios-comparing-ui-design
