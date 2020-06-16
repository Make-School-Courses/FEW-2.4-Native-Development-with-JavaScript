# FEW 2.4 class 5 - Native Components Part 1

Mobile is the land of small screens in portrait orientation. This is a different environment from the desktop. Building mobile apps require developers to think different to work with the limited space. 

## Learning Objectives

- Display data on mobile (lots of data on a small screen)
- Differentiate list view and scrollview and their use cases
- Use a FlatList

## ScrollView vs ListView 

Mobile screens are small you'll always be scrolling. There are two ways to handle scrolling. 

- Scrolling a **small** amount of content
- Scrolling a **large** amount of content

**tl;dr** For a small amount of content use a ScrollView. For a large amount of content use a ListView or Flatlist.

ScrollView scrolls things when the things take up more space than the ScrollView displays.

Why is there a ListView and why would you use one?

The ListView manages a large amount of data. Remember when Steve Jobs said you could have 10,000 songs in your pocket? People though it was great. 

There was a developer somewhere that needed to solve the problem of how to scroll through a list of 10,000 items! 

Seriously, imagine creating 10,000 views and loading them in RAM. Sounds like a memory problem. Heck! imagine rendering the pixels that made up a list of table cells where each cell is 40 pixels tall...

That's a 40,000 pixel tall images! If each cell were 320 pixels wide: 

`40 * 320 * 10,000 = 128,000,000`

By comparison the iPhone SE screen is 320 x 568, thats:

`320 * 568 = 181,760`

So with 10,000 table cells listing all of your favorite songs on your iPhone SE you'd need more than 704 screens!

`128,000,000 / 181,760 = 704.2253521127`

What does the ListView do differently? 

The ListView generates enough views to fill the screen. It displays only a subset of data at any moment. As each row view scrolls off the screen it is recycled and populated with new data. 

## Try it yourself!

For these examples you'll be using a data set that has information about cat and dog breeds. 

Follow the challenges here: https://github.com/Make-School-Labs/few-2-4-by-breed-starter

You can follow the instructions there to get started.

## Implement ScrollView

- Create a scrollView 
- add some content 
- scroll!

Import ScrollView component. 

`import { ScrollView, View, Text } from 'react-native'`

Then import the list of cats, or dogs if you prefer!

`import { cats } from './breeds'`

The `cats` array contains a list of objects with information about a cat breed. 

Something like: 

```JSON
{
	"breed": "Abyssinian",
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

Keep things simple at first. Just make a View and Text component for each breed. 

Make a component: 

```JS 
function Item({ title }) {
  return (
    <View style={styles.item}>
      <Text style={styles.title}>{title}</Text>
    </View>
  );
}
```

Notice this component is using `styles.item`. You can add soem styles for this later. 

In your App.js component use the ScrollView and map the list of cats to Item components. 

```JSX
<ScrollView>
	{cats.map((item, index) => {
		return <Item title={`${index} ${item.breed}`} />
	})}
</ScrollView>
```

When you get this working you may see that it overlaps the status bar at the top or the 'notch' on newer iPhones. 

You can take this into account by adjusting padding an margin on the scrollview. This might prove problematic for the range of phones available. Luckily React Native Provides a `SafeAreaView` component that takes care of this for us! 

import `SafeAreaView`

`import { ..., SafeAreaView } from 'react-native'`

Wrap your `ScrollView` in the `SafeAreaView`. 

```JSX
<SafeAreaView>
	<ScrollView>
		...
	</ScrollView>
</SafeAreaView>
```

- https://reactnative.dev/docs/scrollview
- https://reactnative.dev/docs/safeareaview

## Implement FlatList

- Define data 
- Create a FlatList 
- Define props 
	- renderItem
	- keyExtractor

The FlatFlist is a component that is used to display large amounts of data in a scrolling list. 

The FlatList takes `data` as a prop. Rather than assigning it child components to render you'll give it the data instead. 

FlatList also takes a prop called `renderItem`. This is a function that returns an itme to render. 
	
Why `data`? 

FlatList needs to know how many rows you have to work with. Only a subset of the data will be displayed in the list. FlatList keeps track of the starting and ending indexs that are currently displayed. 
	
Why `renderItem`?

This function returns takes an object with the data and returns a React Native Component which displays as the list cell. FlatList will ask us for the cells it needs, we supply the cell from the data and index. 

The Object passed to renderItem includes three keys: 

- `item` : The `data` item for this row
- `index` : the `index` of this row in `data`
- `separators` : An object with properties that can be used to render separators between rows

Why `keyExtractor`? 

Each cell needs a unique id, `keyExtractor` is a method that generates a unique id for each row. You supply a function that takes two prarameters: 

- `item` : The `data` item for this row
- `index` : The `index` of the row in `data`

Use this function to generate unique row ids. 

## ScrollView demo

- Create ScrollView 
- Fill with objects
- Set styles 
- Options 

## FlatList demo

- Look at the data source 
- Import FlatList
- Render a FlatList
- Set props
	- data
	- renderItem 
	- keyExtractor
- Define a Row Component

The data source includes a list of cat and a list of dogs. Each animal has an object that inlcudes a breed property, and a list of other properties that rate the `breed` in different areas such as: friendliness, Affection, Shedding, Health etc. Each of these fields is rated with a value of 0 to 5. 

**NOTE!** Not all properties appear with every animal. Only `breed` is guaranteed to appear with each object. 

Create the FlatList component. Add set it's props. 

- `data` - Set the data source to an array. 
- renderItem - A function that returns a Component
	- The function takes an object with the following properties: 
		- `item` - An item from data
		- `index` - the index of the item in data
		- `separators` - An object with properties used for customizing custom separator Components (not used in this example)
		
Set data to an array:

```JSX
<FlatList 
	data={cats}
/>
```

Here the array contains data items that rendered into rows in the FlatList. 

Set renderItem: 

```JSX
<FlatList 
	...
	renderItem={({ item, index }) => {
		return <Item title={`${index} ${item.breed}`} />
	}}
/>
```

The `renderItem` function returns a component to display for each row. The function receives an object with the `item` and the `index`. 

The `item` is an element from the data array and `index` is it's position in the array. In this example `item` would be one of the values from data array.

When you get this working you may see a wanring telling you that your list is missing keys. Fix this by defining a key extractor. 

Define `keyExtractor`. React requires all children of a JSX list to have a unique key. `FlatList` handles this with `keyExtractor` which is a function that receives the item to render and returns a unique key.

All of the breeds are unique. You can use that as a key. 

```JSX
<FlatList 
	...
	keyExtractor={item => item.breed}
/>
```

The keyExtractor function generates a unique key for each cell. Here the cell was generated from the contents of the row plus the index. If your data had unique ids you could use those. 

https://reactnative.dev/docs/flatlist#docsNav

## Challenges 
 
1. Customize the `Item` component to display other info related to the breed. 
1. Use Styles to customize the appearance of cells. 
1. Display the other data. Note that each breed doesn't always have the same data/keys as other breeds. You'll need to get the keys and display the data for the available keys. You can use `Object.keys(data)` to get an array of keys on `data`. 
1. Display dogs, if you haven't, cats if you have. 
1. Display both dogs and cats. 
1. Add an option to switch between cats and dogs. You'll need a UI element to choose the pet type. On iOS you can use SegmentedControlIOS. On Android you can use one or buttons, there are also a couple [third party segmented controls](https://stackoverflow.com/questions/35313387/segmentedcontrolios-for-android-in-react-native)

## After class

Complete the challenges [here](https://github.com/Make-School-Labs/few-2-4-by-breed-starter). 

Start defining your custom project. 

## Resources 

- [ScrollView](https://facebook.github.io/react-native/docs/scrollview)
- [FlatList](https://facebook.github.io/react-native/docs/flatlist)
	- [data](https://facebook.github.io/react-native/docs/flatlist#data)
	- [renderItem](https://facebook.github.io/react-native/docs/flatlist#renderitem)
	- [keyExtractor](https://facebook.github.io/react-native/docs/flatlist#keyextractor)
