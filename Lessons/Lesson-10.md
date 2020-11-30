# FEW 2.4 Animation 

Making things move on mobile provides that thing that makes your apps interesting and irresistible. 

## Objectives 

- Define a plan and milestones for your project
- Make things that move on mobile
- Use Animated for discreet animated objects 
- Use LayoutAnimation for animating groups of elements

## Planning your project

To get the best results for your project you need a plan. Do this: 

- Write a short description of your project goals. 
- Make a list of tasks you'll need to complete to complete your project. 
- Take a look at the class calendar in the syllabus and map your tasks across the remaining time. 

Assess at the scope of your project. Ask yourself if it looks like there is too much to complete before the end of the term? 

Take stock of what is in your project and compare to the project description. Do you have all of the required elements?

## Animation

Animation is about making things change over time. On the computer this boils down to changing numeric values over time. The appearance of any component on the screen is controlled by a collection of numeric values. Change these values and the appearance of an object changes. Continuously change the values and it looks like it's moving. 

For the record motion includes changes in: color, opacity, size, shape, and rotation. 

React Native provides two complimentry animation systems: `Animated` for animating specific elements and interactions, and `LayoutAnimation` for animating global layout transactions.

## `Animated`

To animate an object you'll need to change one or more of the values that define it over time. 

For example if you wanted a View to fade in you would animate the opacity of the view from 0 to 1. 

Animated is a built in Component, you'll use it to handle animating other components. Animated has many options.

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

There are several example Components: Animated_1-6 that show introductory examples of motion using animated. 

Create a new React Native project with Expo. 

Try out the following component examples: 

**Fade Animation**

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
    // width: new Animated.Value(0),
    // spin: new Animated.Value(0)
  }

  // Start the animation when this view loads
  componentDidMount() {
    // console.log('Animation 1 Component MOUNTED')
    // 3. Call Animated.timing() and set the ending value, duration, and delay
    
    // Animated.timing(value, options).start()
    Animated.timing(
      this.state.fade, {
        toValue: 1,
        duration: 1000,
        delay: 4000,
        useNativeDriver: true
      }
    ).start() // Start the Animation

    // Animated.timing(
    //   this.state.width,
    //   {
    //     toValue: 200, 
    //     duration: 2000, 
    //     delay: 1000
    //   }
    // ).start()

    // Animated.timing(
    //   this.state.spin, 
    //   {
    //     toValue: 360, 
    //     duration: 3000, 
    //     useNativeDriver: true
    //   }
    // ).start()
  }

  componentDidUpdate() {
    // console.log('Animation 1 Component UPDATED')
  }

  componentWillUnmount() {
    // console.log('Animation 1 Component UNMOUNTED')
  }

  render() {
    // 4. Get the fade value 
    const { fade, width } = this.state

    return (
      <View style={styles.container}>
        {/* Apply the fade value to a CSS property */}
        <Animated.View style={{ 
          ...styles.box, 
          opacity: fade
         }}>
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

**Translation Animation**

```JS
// Move a view by animating the X and Y.

// Moving things requires a little more work. 
// Besides setting the x and y you also need to consider the position 
// determined by layout systems with flex. 

// Here we'll use ValueXY this handles an object with x and y properties. 
// The getLayout() method converts x and y to left and top for positioning. 

// Think of the toValue as an offset relative to where the element would 
// be placed by flex layout. 

// That means that the current position + {x:100, y:50} would place the 
// object 100 pixels to the right and 50 pixels down from where flex 
// would have positioned it.

// The example here uses a starting position of { x:0, y: 400 } that's
// 400 pixels down, and animates it to { x: 0, y: 0 } which should be
// it's position without an offset. 

import React from 'react';
// Import Animated
import { StyleSheet, Text, View, Animated, Easing } from 'react-native';

export default class Animated_2 extends React.Component {
  // Define State that holds the values for the animation. 
  // In this case animating the position of the object with x and y. 
  // The numbers here is starting position. Imagine this as the 
  // offset from where the object would appear without these numebrs. 
  state = {
    move: new Animated.ValueXY({ x:0, y: -400 })
  }
  
  componentDidMount() {
    // Use spring animation
    Animated.timing(
      this.state.move, {
        easing: Easing.in(Easing.bounce),
        toValue: { x: 0, y: 0 }, // toValue consists of x and y
        // Seems to have an error when using native driver true
        useNativeDriver: false
      }
    ).start() // Start the animation
  }
  
  render() {
    const { move } = this.state
    return (
      <View style={styles.container}>
        {/* Combine the styles with move. Call getLayout() to convert x and y to screen coords */}
        <Animated.View style={[styles.box, move.getLayout()]}>
          <Text style={styles.title}>Animated 2</Text>
          <Text>Animation moves up using spring.</Text>
        </Animated.View>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    // Position the object in the center (with no offset). 
    flex: 1,
    alignItems: 'center',
    justifyContent: 'center',
    backgroundColor: '#fff',
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

## Resources 

- https://drop.engineering/demystifying-react-natives-animated-api-part-1-681da7ca4661
- https://www.belatrixsf.com/blog/animations-react-native






