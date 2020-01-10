# FEW 2.4 class 5 - Native Components Part 1

Mobile is the land of small screens in portrait orientation. This is a different environment from the desktop. Building mobile apps require developers to think different to work with the limited space. 

## Learning Objectives

- Display data on mobile
- Differentiate list view and scrollview and their use cases
- Use a FlatList

## ScrollView vs ListView 

Mobile screens are small you'll always be scrollings. There are two ways to handle scrolling. 

- Scrolling a **small** amount of content
- Scrolling a **large** amount of content

**tl;dr** For a small amount of content use a ScrollView. For a large amount of content use a ListView. This is obviously an oversimplified solution but it describes the situation well enough.

ScrollView scrolls things when the things take up more space than the ScrollView displays. Yeah that's what you expected. 

Why is there a ListView and why would you use one?

The ListView manages a large amount of data. Remember when Steve Jobs said you could have 10,000 songs in your pocket? People though it was great. 

There was a developer somewhere that needed to solve the problem of how to scroll through a list of 10,000 items! 

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
	
Why renderItem?

This function returns takes an object with the data and returns a React Native Component that displays as the list cell. FlatList will ask us for the cells it needs, we supply the cell from the data and index. 

The Object passed to renderItem includes three keys: 

- item : The data item for this row
- index : the index of this row in data
- separators : An object with properties that can be used to render separators between rows

Why keyExtractor? 

Each cell needs a unique id, keyExtractor is a method that generates a unique id for each row. You supply a function that takes two prarameters: 

- item : The data item for this row
- index : The index of the row in data

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

The data source includes a list of cat anda list of dogs. Each animal has an object that inlcudes a breed property, and a list of other properties that rate the `breed` in different areas such as: friendliness, Affection, Shedding, Health etc. Each of these fields is rated with a value of 0 to 5. 

NOTE! Not all properties appear with every animal. Only `breed` is guaranteed to appear with each object. 

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
	...
	data={['A', 'B', 'C', 'D']}
	...
/>
```

Here the array contains data items that rendered into rows in the FlatList. 

Set renderItem: 

```JSX
<FlatList 
	...
	renderItem={({item, index}) => <Text>{`${index} ${item}`}</Text>}
	...
/>
```

The renderItem function returns a component to display for each row. The function receives an object with the item and the index. these were displayed with a text component. 

Define keyExtractor: 

```JSX
<FlatList 
	...
	keyExtractor={(item, index) => `${item}-${index}`}
	...
/>
```

The keyExtractor function generates a unique key for each cell. Here the cell was generated from the contents of the row plus the index. If your data had unique ids you could use those. 

## Challenges 

Use the starter project starter code [here](https://github.com/Make-School-Labs/by-breed-starter).

- Use the cat or dog data in place of the Array of strings used in the example. 
- Create a custom function for each row. Return this from renderItem.
- Style the row component
- Display the data from the cat/dog object. 

## After class

- Define a project for yourself it should be native either desktop or mobile
- Create a set of milestones. 
	- List these by class number with completed project done on class 14. 

## Resources 

- [ScrollView](https://facebook.github.io/react-native/docs/scrollview)
- [FlatList](https://facebook.github.io/react-native/docs/flatlist)
	- [data](https://facebook.github.io/react-native/docs/flatlist#data)
	- [renderItem](https://facebook.github.io/react-native/docs/flatlist#renderitem)
	- [keyExtractor](https://facebook.github.io/react-native/docs/flatlist#keyextractor)
