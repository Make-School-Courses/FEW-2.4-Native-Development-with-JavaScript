# FEW 2.4 Animation 

Making things move on mobile provides that thing that makes your apps interesting and irresistible. 

## Objectives 

- Make things that move on mobile
- Use Animated for discreet animated objects 
- Use LayoutAnimation for animating groups of elements

## Animation

Animation is about making things change over time. On the computer this boils down to changing numeric values over time. The appearance of any component on the screen is controlled by a series of numeric values. Change these values and and the appearance of the things changes. Continuously change the values and it looks like it's moving. 

For the record motion includes changes in color, opacity, size, shape, and rotation. 

While you could changes values using timers React Native has provides more abstract systems for making things move.

React Native provides two complimentry animation systems: `Animated` for animating specific elements and interactions, and `LayoutAnimation` for animating global layout transactions. 

## `Animated`

Animation is making things move on the screen. Behind the scenes this is handled by changing values over time. 

For example if you wanted a view to fade you would animate the opacity of the view from 0 to 1. 

Animated is a built in Component, you'll use it to handle animating other components. 

Animated has many options!

**Use Animated for discreet animations**. This would be single elements that move or change. 

### Example

```JS
// A simple animation. This example fades a view in by animating 
// the opacity

// 1. Import Animated from react native 
// 2. Define a property to be animate
// 3. Define and start an Animation
// 4. Use the animated to value 

import React from 'react';
// 1. Import Animated
import { StyleSheet, Text, View, Animated } from 'react-native';

export default class Animated_1 extends React.Component {
  // 2. Define a value to animate on state: fade with an initial value of 0
  state = {
    fade: new Animated.Value(0),
  }

  // Start the animation when this view loads
  componentDidMount() {
    // 3. Call Animated.timing() and set the ending value, duration, and delay
    Animated.timing(
      this.state.fade, {
        toValue: 1,
        duration: 3000,
        delay: 1000
      }
    ).start() // Start the Animation
  }

  render() {
    // 4. Get the fade value 
    const { fade } = this.state
    return (
      <View style={styles.container}>
        {/* Apply the fade value to a CSS property */}
        <Animated.View style={{ ...styles.box, opacity: fade }}>
          <Text style={styles.title}>Animation 1</Text>
          <Text>Fades in using Animated</Text>
        </Animated.View>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
  box: {
    backgroundColor: 'rgba(255, 0, 0, 0.5)',
    width: 200,
    height: 200,
    display: 'flex',
    justifyContent: 'center',
    alignItems: 'center'
  },
  title: {
    fontSize: 24,
    fontWeight: 'bold'
  }
});
```

Here is the same example written with a hooks. This example uses `useEffect()` a React Hook that handles lifecycle events. 

https://medium.com/recraftrelic/usestate-and-useeffect-explained-cdb5dc252baf

https://leewarrick.com/blog/react-use-effect-explained/


```JS

// A simple animation. This example fades a view in by animating 
// the opacity

// 0. Import Hooks useEffect and useRef
// 1. Import Animated from react native 
// 2. Define a property to be animate
// 3. Define and start an Animation
// 4. Use the animated to value 

// 0. Import some hooks 
import React, { useEffect, useRef } from 'react';
// 1. Import Animated
import { StyleSheet, Text, View, Animated } from 'react-native';

export default function Animated_1_hooks() {
  // 2. Define a value to animate on state: fade with an initial value of 0
  const fadeAnim = useRef(new Animated.Value(0)).current 
  
  // This acts as a lifecycle method
  useEffect(() => {
    Animated.timing(
      fadeAnim,
      {
        toValue: 1,
        duration: 5000,
      }
    ).start();
  }, [])

  return (
    <View style={styles.container}>
      {/* Apply the fade value to a CSS property */}
      <Animated.View style={{ ...styles.box, opacity: fadeAnim }}>
        <Text style={styles.title}>Animation 1</Text>
        <Text>Fades in using Animated</Text>
      </Animated.View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
  box: {
    backgroundColor: 'rgba(255, 0, 0, 0.5)',
    width: 200,
    height: 200,
    display: 'flex',
    justifyContent: 'center',
    alignItems: 'center'
  },
  title: {
    fontSize: 24,
    fontWeight: 'bold'
  }
});
```


## Demo Example 

Follow the example here: https://github.com/Make-School-Labs/react-native-animation-examples

There are several example Components: Animated_1-6 that show introductory examples of motion using animated. 

## Resources 

- 





