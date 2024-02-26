---
layout: post
title: "Lecture 7 : MVVM"
permalink: /lectures/mvvm/
categories: notes
---
The Model-View-ViewModel (MVVM) pattern is a *software design pattern*. Design patterns are sets of rules and templates that help make application code better or more consistent. 

- The MVVM pattern is used to help separate the app's behavior logic from the user interface-rendering code, and to do so in a way that supports unit testing.
- MVVM is the basis for many frameworks and programming tool-kits. Most of those frameworks also provide other things, like navigation and messaging abstractions, that help MVVM promote unit testing. 

## MVVM & `.NET MAUI`

- `.NET MAUI` apps that do not use MVVM generally have more code in their *code-behind* files. 
  - The code-behind files follow this pattern: *{something}.xaml.cs*. 
  - Most code in the code-behind file usually controls the user interface (UI) behavior. *UI behavior* can include anything that happens *to* the UI, like changing a color or some text. 
  - Code-behind file can include anything that happens *because of* the UI, including button click handlers.
- What is the problem in using code-behind files?
  - One problem with this approach is that it is hard to write unit tests against code-behind files. 
  - Code-behind files in a `.NET MAUI` app derive from a `.NET MAUI` framework type. They often assume an application state that is created by parsing XAML or even created by other pages. These conditions are difficult to handle in a unit test runner that might not even be running on a mobile device, let alone with a user interface. So, unit tests are rarely able to test the UI behaviors in these files.
- Why and when to use MVVM?
  - When used correctly, the MVVM pattern solves these problems by moving most UI behavior logic to unit-testable classes that are called `viewmodels`. 
  - The MVVM pattern is most commonly used with frameworks that support data-binding. 
  - In `.NET MAUI`, each UI element can data-bind to a `viewmodel` and eliminate or nearly eliminate code in a view or code-behind.

## Parts of an MVVM application

### Model

In an MVVM application, the *model* refers to your business data and business logic. The model does not concern how the app is presented to the user.

A good guideline for defining what code goes in the model is that you could port your application from mobile app to the web or to a command-line program and use the same *model* in all three places. It has nothing to do with presentation to the user.

When you think about an application, the model would include a class of an item used in a collection. The model could also include things like a `Repository` class that holds persistence logic. Some other software-design patterns would consider things like *repositories* as separate from the model. 

### View

The *view* code controls things that directly interact with the user. Usually that means changing pixels on the screen and receiving clicks and taps. View items include controls like buttons and entry fields, as well as any other purely visual elements like themes, styles, and fonts.

In many `.NET MAUI` apps, you do not need to write any C# code for views yourself. Instead, your views are often defined by your `.xaml` files. Of course, there are situations that call for a custom user control. In those cases, you can create your own view code. 

### ViewModel

The viewmodel is the intermediary between our business logic and the app views.



As shown above the viewmodel exposes properties to the user interface. Viewmodels usually rely on models for most of their data and any business logic. In addition, it is the viewmodel that formats, converts, and enriches the data in whatever way the current view requires.