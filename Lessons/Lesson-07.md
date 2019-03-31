# FEW 2.4 class 7 - Native Components Part 1
## Learning Objectives/Competencies

- Use List View 
- Use Scroll View 
- Differentiate the differences and use cases for List and Scroll views 

## ScrollView vs ListView 

Mobile screens are small you'll always be scrollings. There are two ways to handle scrolling. 

- Scrolling a **small** amount of content
- Scrolling a **large** amount of content

**tl;dr** For a small amount of content use a ScrollView. For a large amount of content use a ListView. 

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

Thw ListView generates enough views to fill the screen. It displays only a subset of data at any moment. As each row view scrolls off the screen it is recycled and populated with new data. 

















- Discussion Android and iOS
	- Who uses Android? 
		- What are the UI systems in use? 
	- Who uses iOS?
		- What are UI systems in use? 

Simple Navigation 

- Conceptual 
	- One dimensional 
	- Uses a single navigation stack 
	- Modals
	- [HIG iOS](https://developer.apple.com/design/human-interface-guidelines/ios/overview/interface-essentials/)
	- [Material Android](https://material.io/design/introduction/#principles)
- Practical 
	- List detail view 

More detailed Navigation 

- Conceptual 
	- Multi-dimensional
	- Uses tabs 
	- Nested Navigation stacks 
		- tl;dr the stacks to dont' cross over







	
## Native Android and iOS components 

Demo project look at 

## Overview/TT II (optional)

## In Class Activity II (optional)

## After Class

- Continue working on your current tutorial
- Complete reading
- Complete challenges

## Additional Resources

- Compare Android and iOS
	- https://medium.com/@chunchuanlin/android-vs-ios-compare-20-ui-components-patterns-part-1-ad33c2418b45
	- https://medium.com/@vedantha/interaction-design-patterns-ios-vs-android-111055f8a9b7
	- https://www.ready4s.com/blog/android-vs-ios-comparing-ui-design
