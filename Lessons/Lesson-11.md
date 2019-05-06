# FEW 2.4 Animation 

Making things move on mobile provides that thing that makes your apps interesting and irresistible. 

## Objectives 

- Make things that move on mobile
- Use Animated for discreet animated objects 
- Use LayoutAnimation for animating groups of elements

## Animation

Animation is about making things change over time. On the computer this boils down to changing numeric values over time. The appearance of any component on the screen is controlled by a series of numeric values. Change these values and and the appearance of the things changes. Continuously change the values and it looks like it's moving. 

For the record motion includes changes in color and opacity, size, shape, and rotation. 

While we could changes values using timers React Native has provides more abstract systems for making things move.

React Native provides two complimentry animation systems: `Animated` for animating specific elements and interactions, and `LayoutAnimation` for animating global layout transactions. 

## `Animated`

Animation is making things move on the screen. Behind the scenes this is handled by changing values over time. 

For example if you wanted a view to fade you would animate the opacity of the view from 0 to 1. 

Animated is a built in Component, you'll use it to handle animating other components. 

`import { Animated } from 'react-native'`

Define a property to animate on state. This example will animate the opacity of a component. 

```JS
state = {
	fade: new Animated.Value(0),
}
```

Start the animation by defining the starting value, and providing a config object. The config object sets the `duration` and the `toValue`.







