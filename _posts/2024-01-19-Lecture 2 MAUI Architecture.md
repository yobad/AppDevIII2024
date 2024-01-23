---
layout: post
title: "Lecture 2: .NET MAUI"
categories: misc
---
Those notes are based on: 
[Microsoft's documentation](https://learn.microsoft.com/en-ca/dotnet/maui/what-is-maui?view=net-maui-8.0) 
### Architecture of .NET MAUI


<img src="{{site.baseurl}}/images/maui_intro/maui_architecture.png" height=500 />
# Structure of a .NET MAUI Project

- Open Visual Studio 2022

- Create a .NET MAUI Application

- Overview of the project explorer

- Platforms: This folder contains platform specific code:

  

- After building your project, if you navigate to the location of the bin folder of the project, you can find multiple applications created for the app.

- Typically there's a resource's folder in which all images, fonts, etc. are stored. MAUI will be responsible of embedding this content to each platform with its specificity.  

- Shell

- Pages

- Layouts

- Controls

- Data Binding

- Access to device features (cameras, sensors, location, etc.)
