---
layout: post
title: "Lecture 2: .NET MAUI"
categories: misc
---
Those notes are based on: 
[Microsoft's documentation](https://learn.microsoft.com/en-ca/dotnet/maui/what-is-maui?view=net-maui-8.0) 
### Architecture of .NET MAUI

- .NET MAUI stands for .NET Multi-platform App UI.
- It's a relatively new cross-platform framework from Microsoft.
- Shared code base for iOS, Androidm MacOs and Windows.
- Very well intgrated with Visual Studio. 
- Programming language: C# (already cross-platform!)
- UI page definition uses Xaml which is a declaratif language (you've already seen this in previous courses!)


# How does it work?
- Abstracts the details specific to each platform using platform-specific framewors: .NET Android, .NET iOS, .NET macOs, WinUI 3 (Windows)
- Uses a unified interface called .NET Base to interact with each of these frameworks.
- The business logic and common UI elements of your App will be using this interface.

<img src="{{site.baseurl}}/images/maui_intro/maui_architecture.png" height=500 />

- For Android, iOs and MacOs, the execution environment is implemented in Mono.
- For Windows, the execution environement is .NET CoreCLR.

# Structure of a .NET MAUI Project

1. Open Visual Studio 2022

2. Create a MAUI App from the project templates
<img src="{{site.baseurl}}/images/maui_intro/maui_template.png" height=500 />

3. Choose a name and location to your new MAUI app.

4. Select the latest .NET framework available. It should be .NET 6.0 or 8.0 (Long term Support)

5. Press the Play button to build the project on your Windows computer:
<img src="{{site.baseurl}}/images/maui_intro/run_windows.png" />

5. You should now see the MAUI template project app:
<img src="{{site.baseurl}}/images/maui_intro/Maui_windows.png" />

6. On File Explorer, navigate to your `<project folder>/bin/Debug/`, you should see multiple folders on which your app can be deployed. For now, the only folder that contains a deployed solution is the Windows folder:   
<img src="{{site.baseurl}}/images/maui_intro/debug_folder.png" />

7. Open 


Overview of the project explorer

- Platforms: This folder contains platform specific code:
<img src="{{site.baseurl}}/images/maui_intro/project_explorer.png" />
  

- After building your project, if you navigate to the location of the bin folder of the project, you can find multiple applications created for the app.

- Typically there's a resource's folder in which all images, fonts, etc. are stored. MAUI will be responsible of embedding this content to each platform with its specificity.  



# What is XAML?

- XAML is a declarative markup language which defines the UI components of the App.
- It's also used in WPF and UWP.
- Extension is `.xaml`
- For every xaml file, you have an associated C# code behind with the same name:
<img src="{{site.baseurl}}/images/maui_intro/code_behind.png" height=500 />

The MainPage.xaml:

