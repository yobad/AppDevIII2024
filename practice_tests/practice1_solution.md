---
layout: post
title: "Practice Test 1"
permalink: /practicetests/practice1_solution
categories: labs
---

**CPAD** 

1. True or False, when using the .NET MAUI the logic is coded in C# and the platform-specific UI is written in XAML. 

**False, cross-platform code is written in both C# and XAML and platform specific code can also be written in C# and XAML.**

1. True or False, Flutter uses dart and Flutter widget? 

**True, logic is written in dart and the UI is written with Flutter widget.**

1. True or False, C# based Xamarin framework was renamed to MAUI? 

**False, although MAUI is based on Xamarin Forms and uses a similar architecture XAML/C# , MAUI has many new and improved features. Various features of Xamarin are also obsolete in MAUI. ** 

1. True or False, React Native produces native apps? 

**True, React Native is based on the React framework which generates native controls.** 

1. True or False, React Native uses React Native views which are compiled to their corresponding views on their respective platforms. 

**True, as with all Cross-platform native frameworks, a single code base is compiled for various platforms which generates a different native app for its respective platform.**

1. True or False, Flutter is based on UI Widgets, which will then be transformed into native UI by Dart. 

**False, Flutter is not a native cross-platform framework. The result is a progressive web app which mimics the native controls but is based on web technology. **

1. True or False, PWA are very similar to responsive Web Sites only they are available offline. 

**False, PWA may be confused with responsive website but there is a few significant differences other than offline accessibility. PWA have their own icon on the mobile screen. PWA tend to mimic the native app experience by offering push notifications, access to the camera, GPS, and other mobile features. They are running directly on the device and not on a Web server.  **

1. Associate the best cross-platform framework with the scenario. 

- A company has a Web application developed in HTML, CSS and JavaScript. A new business need requires this application to also be available in Mobile. **Cordova**

- A startup wants to develop an app to go with their product, most of their clients are iOS users.  **Swift**

- A gaming company wants to develop an App mainly for Windows that needs to interface directly with the hardware. **C++ /Win32**

- A mobile gaming company would like to create a game for various platforms.  **.NET MAUI** or **React Native**

- The government of Canada wants to create a vaccination passport application deployed across platforms and accessible via browsers. **Flutter**

  

**MAUI Architecture**  

1. Explain briefly how does the MAUI framework work?

**.NET MAUI uses a unified interface called .NET Base to create a common business logic and a common user interface, the apps will be compiled on the various platforms using an execution environment which then translates it into platform specific code. The end goal is to maintain a single code base while being able to easily deploy on a variety of operating systems and platforms **

1. True or False, MAUI Apps are slightly less performant than native apps.

**True, .NET MAUI  doesn't directly use CoreOS libraries to interact with the hardware which may introduce inefficiencies when running resource intensive tasks**  



**Data Binding** 

1. Explain briefly what is data binding and what design pattern is it based on?

   **Data Binding is a mechanism offered in .NET MAUI (and other frameworks) to link the behavior of an observed object and its properties to a subscriber object and its properties. This is a based on the IoC (Inversion of Control). IoC is a design pattern which allows the flow of execution of a program to be controlled by the framework by contrast with procedural programs where all steps of executions are determined within the main program. This enables the use of callback when a certain event occur.** 

2. The following XAML to XAML binding is not working, explain what is incorrect:

   ```xml
    <Slider x:Name="slider" Minimum="1" Maximum="360"/>
               <Label Text="{Binding slider.Value, StringFormat='Value of slider is: {0:F4}'}"/>
   ```

   **The Label in this case doesn't have a binding context and the "slider" is not found. To reference the slider we need to use the Markup extension `x:Reference`**

Possible fix 1:

```xml
    <Slider x:Name="slider" Minimum="1" Maximum="360"/>
    <Label Text="{Binding Value, StringFormat='Value of slider is: {0:F4}'}" BindingContext="{x:Reference slider}"/>
```

Possible fix 2:

```xml
    <Slider x:Name="slider" Minimum="1" Maximum="360"/>
    <Label Text="{Binding Source={x:Reference slider}, Path=Value, StringFormat='Value of slider is: {0:F4}'}" />
```



**Asynchronous programming**

Re-write the following synchronous code to make tea in an asynchronous way:



**Solution:**

```csharp

class Program
{        
    static async Task  Main(string[] args)
    {
        //Asynchronous version of making tea.
        Console.WriteLine(" >>> Asynchronous version of making tea");

		await MakeTeaAsync();
		
		Console.WriteLine(" **** **** ***** ");

    }
    
    static async Task<string> MakeTeaAsync()
    {
        Console.WriteLine("Tea Process >>> Fill Kettle");
        Task<string> waterTask = BoilWaterAsync();
        Console.WriteLine("Tea Process >>> Take cup out");
        Console.WriteLine("Tea Process >>> Add Tea to cup");
        string water = await waterTask;
        string tea = $"Pour {water} in cup";
        Console.WriteLine(tea);

        return tea;
    }
    
    
    static async Task<string> BoilWaterAsync()
    {
        Console.WriteLine("Boil Process >>> Start the kettle");
        Console.WriteLine("Boil Process >>> Waiting for the kettle");
        await Task.Delay(3000); //Delay representing the delay boiling water
        Console.WriteLine("Boil Process >>> Finished boiling");
        return "Boil Process >>> Hot water";

    }
```

