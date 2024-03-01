---
layout: post
title: "Practice Test 1"
permalink: /practicetests/practice1
categories: labs

---

**CPAD** 

1. True or False, when using the .NET MAUI the logic is coded in C# and the platform-specific UI is written in XAML. 
2. True or False, Flutter uses dart and Flutter widget? 
3. True or False, C# based Xamarin framework was renamed to MAUI? 
4. True or False, React Native produces native apps? 
5. True or False, React Native uses React Native views which are compiled to their corresponding views on their respective platforms. 
6. True or False, Flutter is based on UI Widgets, which will then be transformed into native UI by Dart. 
7. True or False, PWA are very similar to responsive Web Sites only they are available offline. 
8. Associate the best cross-platform framework with the scenario. 



**MAUI Architecture**  

1. Explain briefly how does the MAUI framework work?
2. True or False, MAUI Apps are slightly less performant than native apps.

**Data Binding** 

1. Explain briefly what is data binding and what design pattern is it based on?

2. The following XAML to XAML binding is not working, explain what is incorrect:

   ```csharp
    <Slider x:Name="slider" Minimum="1" Maximum="360"/>
               <Label Text="{Binding slider.Value, StringFormat='Value of slider is: {0:F4}'}"/>
   ```

   



**Asynchronous programming**

Re-write the following synchronous code to make tea in an asynchronous way:

```csharp

class Program
{        
    static async Task  Main(string[] args)
    {
        //Synchronous version of making tea.
        Console.WriteLine(" >>> Synchronous version of making tea");
        MakeTea();
        Console.WriteLine(" **** **** ***** ");

        //Asynchronous version of making tea.
        Console.WriteLine(" >>> Asynchronous version of making tea");










    }

    static string MakeTea()
    {
        Console.WriteLine("Tea Process >>> Fill Kettle");
        string water = BoilWater();
        Console.WriteLine("Tea Process >>> Take cup out");
        Console.WriteLine("Tea Process >>> Add Tea to cup");
        string tea = $"Pour {water} in cup";
        Console.WriteLine(tea);

        return tea;
    }

    static string BoilWater()
    {
        Console.WriteLine("Boil Process >>> Start the kettle");
        Console.WriteLine("Boil Process >>> Waiting for the kettle");
        Task.Delay(3000); //Delay representing the delay boiling water
        Console.WriteLine("Boil Process >>> Finished boiling");
        return "Boil Process >>> Hot water";

    }

```

