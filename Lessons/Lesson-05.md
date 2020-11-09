# FEW 2.4 - React Native - Native Components

## Learning Objectives/Competencies

- Use native components to build mobile applications
	- Use the View, Text, SafeAreaView, ScrollView, and FlatList components
- Apply styles to components 
	- Use Flex Box, to arrange elements on the screen
	- Use flex, width, height, padding, margin, and border to define the appearance of elements on the screen
- Define applicqation structure with Components 
- Use Object.keys() 

## Components Reviewed

- View
- Text
- SafeAreaView
- ScrollView
- 

## View 

Defines a reactangular area on the screen. Use it like you might use a `<div>` in a web project. 

## Text 

Use the Text component to display text. Use it with styles to create text blocks, headlines, titles, and labels. 

## Put View and Text together

Put the View and Text native components together to display a block. In this example you'll make a cell that will display as a single row in a list. The first step will be to display one Cell later you will make a list. 

### Make a Cell

The Cell will be a component made of a View and two Text components. 

```JS 
import React from 'react';
import { StyleSheet, Text, View } from 'react-native';

export default function Cell({ name, subtitle }) {
  return (
    <View style={styles.container}>
      <Text style={styles.h1}>{name}</Text>
      <Text style={styles.body}>{subtitle}</Text>
		</View>)
}
```

Display a Cell in your App component to test it: 

```JS
import Cell from './components/Cell'
...
<Cell title="Hello World" subtitle="Foo Bar" />
...
```

### Style the Cell

In the Cell.js add some inline styles. 

All elements are display Flex. 

```JS
const styles = StyleSheet.create({
  container: { // Think of these properties like CSS classes
    width: '100%', // You can use % as a unit
		padding: 10,   // Other values don't use a unit!
    backgroundColor: '#ff0', // Non numeric values are quoted
    // display: 'flex', // All elements are display Flex
    alignItems: 'flex-start',
    justifyContent: 'center',
		borderBottomWidth: 1,
		borderBottomColor: '#ddd'
  },
  h1: {
    fontSize: 30,
    textAlign: 'left',
    marginBottom: 5
  }, 
  body: {
		// Add some styles here for the sub title
  }
});
```

Apply styles like this. 

```JS
export default function Cell({ title, subtitle }) {
  return (
    <View style={styles.container}> 
      <Text style={styles.h1}>{title}</Text>
      <Text style={styles.body}>{subtitle}</Text>
		</View>)
}
```

All styles are applied inline. 

## SafeAreaView 

When displaying elements on mobile devices we need to be aware the status bar which can vary in size across different platforms and models of phone. 

Luckily React Native provides a `SafeAreaView` that takes care of this for us. 

In your App.js import the `SafeAreaView` and make it the top level component in App. If you have a View in App already you can replace it with `SafeAreaView`.

```JS
...
import { StyleSheet, SafeAreaView } from 'react-native';
import Cell from './components/Cell'

export default function App() {
  return (
    <SafeAreaView style={styles.container}>
      <Cell title="Hello World" subtitle="Foo Bar" />
    </SafeAreaView>
  );
}
...
```

Using SafeAreView should make the Cell clear the status abr and this should adjust it self for differences in devices. 

## Use ScrollView 

The ScrollView component creates a scrolling block of content. Just wrap some content in a `ScrollView`. 

### Make a ScrollView

Place the a ScrollView and some content inside your App. 

```JS
export default function App() {
  return (
    <SafeAreaView>
      {/* <Cell title="Hello World" subtitle="Foo Bar" /> */}

      <ScrollView>
        <Cell title="Hello World" subtitle="Foo Bar" />
        <Cell title="Hello World" subtitle="Foo Bar" />
        <Cell title="Hello World" subtitle="Foo Bar" />
        <Cell title="Hello World" subtitle="Foo Bar" />
        <Cell title="Hello World" subtitle="Foo Bar" />
      </ScrollView>
		</SafeAreaView>
	)
}
```

Here you should be able to scroll the list if cells. 

The ScrollView is used to create scrolling blocks of content. If you're creating a large list of elements you should use the ListView. 

## List Views

List Views manage long lists of many elements efficiently. React Native provides two List Views: `FlatList` and `SectionList`. Let's implement `FlatList`. 

The list view manages a an array of data and creates a list from the array. 

### FlatList

This example uses the cat or dog data from the starter code and generates a list of Cell components for each animal. 

```JS
<FlatList 
	style={{width: '100%'}}
	data={cats}
	renderItem={({index, item}) => {
		return <Cell title={item.breed} subtitle={index} />
	}}
/>
```

Notice I gave the list a style with width 100%. This is important to make the list fill the width of the screen. 

The `data` prop should be an array of data you want to display the list. In our example this is an array of objects. 

The `renderItem` prop is a function that will take in the index and an item from the data list and return a component to render as a row in the list.

Since this is React you should provide a key for each element in a list. Since it's React Native you'll won't use a `key` prop and use `keyExtractor` instead. 

```JS
<FlatList 
	...
	keyExtractor={item => item.breed}
/>
```

add `keyExtractor` as a prop and assign it a function that returns a unique value for each item in the list. This function receive the item from the data list. Since our Breed names are unique we can return that here for a keys.

## Displaying Cat and Dog data

Each of the animal objects has a of properties. These are not the same for each animal. The properties are also held in an object on keys not in an array. 

### Getting all the keys

Use `Object.keys(someObject)` to generate an array of keys.

```JS
"Abyssinian": {
	"Affectionate with Family": 3,
	"Amount of Shedding": 3,
	"Easy to Groom": 3,
	"General Health": 2,
	"Intelligence": 5,
	"Kid Friendly": 5,
	"Pet Friendly": 5,
	"Potential for Playfulness": 5
}
```

Imagine that `cat` in the code below is an object like the one shown above. The code below turns the features into Text components

```JS
const cat = { ... }
const keys = Object.keys(cat)
const features = keys.map((key, index) => {
	return (
		<Text>{key}: {cat[key]}</Text>
	)
})
```

## By Breed project

Continue working on the By Breed project. 

- [Assignment-4-mobile-app.md](../Assignments/Assignment-4-mobile-app.md)