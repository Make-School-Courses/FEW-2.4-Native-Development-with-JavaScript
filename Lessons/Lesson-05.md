# FEW 2.4 Class 5 - React Native

## Learning Objectives/Competencies

- Define use cases for web vs mobile 
- Identify differences in development between Android and iOS
- Using Native Components
- Building and running apps with Expo
- Compare and contrast testing in the simulator vs testing on a device

## Initial Exercise

- What is React Native?
    - What is Native?
    - Why build a native app?
    - Why build a Web app?
    - What is the user experience web vs native?
        
### Compare Android and iOS UI design

- https://medium.com/@chunchuanlin/android-vs-ios-compare-20-ui-components-patterns-part-1-ad33c2418b45

Take a quick look at the article above. Discuss the differences with a partner. Ideally, pair Android and iOS users. Use your mobile device to help answer the questions. 

Answer these questions: 

- Are there any similarities? 
- What are the major differences? 
- What does this mean for the developer? 

## What is React Native? 

It's a tool from the Facebook team. It uses React to create truly native apps. 

You create apps using the same React Component architecture. The components you create are translated into native code. 

The app logic you write is written in JavaScript. React native implements a subset of the standard browser JavaScript API that maps to native systems. 

This means not everything is supported, if supported you can most likely work with a feature in the same way you would have worked with it in regular JS project. 

Create your first React Native project by following the guide [here](https://facebook.github.io/react-native/docs/getting-started). 

## Styling React Native 

React Native components are styled with a style object using CSS properties. 

Not all properties are supported. Each component only supports a subset of CSS properties. Be sure to look at the documentation for each component to see what properties it supports and how to use that property. 

Why? These components are translated to native code. CSS is used here as an interface to the native code. 

## React Native 

Working with Native projects is a little more complex than working with Web projects. Native projects require a few more tools. These tools compile native code to the target platform, serve the project, and simulate native hardware. 

You'll need to have Node.js 8+ for running the dev server and compiling your JS code. 

- Check that you have this installed

To work with React Native you'll need to have the command-line tool to create and run projects on your computer. 

To test the projects on your phone, Android or iOS, you'll need to install the [Expo](https://expo.io/learn) App. 

- Install it now
    - [Expo Android](https://play.google.com/store/apps/details?id=host.exp.exponent&referrer=www)
    - [Expo iOS](https://itunes.apple.com/app/apple-store/id982107779)

To test your app in a simulator on your computer you'll need to install Xcode and or Android Studio. 

To build and publish your app you'll need to Xcode for iOS and or Android Studio. 

You can skip these steps for now if you have Expo on a mobile device. 

To publish your native apps to the Apple App Store you'll need to have Apple Developer Account. 

This sounds like a lot, and it is, compared to web projects. This is one of the burdens of native dev. 

The easiest path to development is to test on your device using the Expo App. Not only does React Native make this process streamlined and easy to work with, but it also allows you to see your app as it will appear on a real device which is a great way to test. 

Follow the [Quickstart Guide](https://facebook.github.io/react-native/docs/getting-started). 

## In Class Activity I

- Build a simple UI with styles. Use the following native components. Be sure to look them up in the [docs](https://facebook.github.io/react-native/docs/getting-started)!
    - View
    - Text
- Use styles to style the components. Use Flexbox for layout. Be sure to consult the docs to find the supported CSS properties!
    - flex
    - width
    - fontSize
    - color
    - backgroundColor

- Build tip calculator with React Native. Use these components: 
    - View 
    - Text
    - TextInput
    - Button

## After Class

As an intro to React Native do this tutorial. It covers Native Components, Styling Native Components, networking, and geolocation.

- [Wthr Tutorial](https://www.makeschool.com/academy/track/standalone/wthr-native-tutorial-mvs/getting-started)

This tutorial is short, your goal is to complete it this week. 

## Additional Resources

- [React Native](https://facebook.github.io/react-native/)
- [React Native - Quick Start](https://facebook.github.io/react-native/docs/getting-started.html)
- [Wthr Tutorial](https://github.com/MakeSchool-Tutorials/FEW-2.4-Wthr-Native-Tutorial)
