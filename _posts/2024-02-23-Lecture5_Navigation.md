---
layout: post
title: "Lecture 5 : MVVM"
permalink: /lectures/navigation/
categories: notes
---


[TOC]



- One of the very first steps in designing an app is planning how to navigation in and out of the various pages.
- You're first project milestone will be creating a mockup of the app including how the user should navigation across pages.
- So far we've used `Navigation.Pushasync()` to push new pages on the stack
- There exists four  ways of navigating through pages:
  - Tab bar navigation
  - Flyout menu navigation
  - Stack Navigation (**what we've been using so far**)
  - Route Navigation 



# Stack Navigation



- In Lab0, we used `Navigation.PushAsync(new Page());` to push a new page on the stack

- This type of navigation is called "Stack Navigation" or modal navigation

- Other methods exist under the same `INavigation` interface:

  - `PushModalAsync`
  - `PopAsync`
  - `PopModalAsync`
  - `RemovePage`(doesn't work on Android)
  - `PopToRootAsync`

- It's especially useful when the app has a specific flow: y

  - You need to finish one task before moving to the next one 
  - Or, you can't get to the previous task until you are done with this current one.

- In order to remove the current page, we would use `Navigation.PopAsync();`

  

  <img src="{{site.baseurl}}/images/maui_navigation/navigation_pushing.png" Height="100" class="inline-img"/>

  <img src="{{site.baseurl}}/images/maui_navigation/navigation_popping.png" Height="100" class="inline-img"/>

  [^1]: Images found on Xamarin.Forms Model Pages https://learn.microsoft.com/en-us/xamarin/xamarin-forms/app-fundamentals/navigation/modal

  



# Shell

- It's a`XAML` Page that "provides the fundamental UI features that most app require"

- The app shell provides a different interface for navigation

- The shell provides a `skeleton` of your app, this is where you can define the hierarchy of the views 

- You can define a `FlyoutMenu` and/or a `TabBar`

- You can include all your pages and specify routes for those pages

- You can define the look and feel of the `NavBar`

- But! It's more complex than Stack Navigation.

  

# Flyout Navigation

If you wish to access the views used in this demo clone the `Demos` repos

- The Flyout is sometimes called "hamburger" menu and is often represented with this icon:

  <img src="{{site.baseurl}}/images/maui_navigation/flyout_hamburger.png" Height="100" class="inline-img"/>
  
  <img src="{{site.baseurl}}/images/maui_navigation/flyout_1.png" Height="100" class="inline-img"/>
  
  

- When clicking on the icon a side bar appears with clickable items allowing the user to navigate to other pages in the app

## Creating a simple `FlyoutMenu`

- To create a flyout menu within your .NET MAUI app, open to the `AppShell.xaml` file:
- The default MAUI project only contains a `ShellContent` routing to the main page:

```xaml
<Shell
    x:Class="DemoNavigation2.AppShell"
    xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
    xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
    xmlns:local="clr-namespace:DemoNavigation"
    Shell.FlyoutBehavior="Disabled">

<ShellContent
    Title="Home"
    ContentTemplate="{DataTemplate local:MainPage}"
    Route="MainPage" />

</Shell>

```



- Remove the line `Shell.FlyoutBehavior="Disabled"` to enable the flyout behavior

- You can now add more `ShellContent` and you'll notice that I flyout menu appears on the top left corner containing a route to the `MainPage` twice:

```xaml
<Shell
    x:Class="DemoNavigation2.AppShell"
    xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
    xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
    xmlns:local="clr-namespace:DemoNavigation">

<ShellContent
    Title="Home"
    ContentTemplate="{DataTemplate local:MainPage}"
    Route="MainPage" />
<ShellContent
    Title="Home"
    ContentTemplate="{DataTemplate local:MainPage}"
    Route="MainPage" />
    
</Shell>
```



- To be able to refer to the views inside the  `./Views` folder,  add the `xmlns:views` namespace to  `AppShell`:

```xaml
<Shell
    x:Class="DemoNavigation2.AppShell"
    xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
    xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
    xmlns:local="clr-namespace:DemoNavigation"
    xmlns:views="clr-namespace:DemoNavigation.Views">

```



- You can now include views inside this folder, and make use of the `Icon` property to give the flyout menu a nicer look

  ```xaml
      <ShellContent
          Title="Home"
           Icon="home.png"
          ContentTemplate="{DataTemplate local:MainPage}"
          Route="MainPage" />
      <ShellContent
          Title="Info"
          Icon ="setting.png"
          ContentTemplate="{DataTemplate views:InfoPage}"/>
  ```

- Add two more pages to get this result:

  <img src="{{site.baseurl}}/images/maui_navigation/flyout_1.png" Height="100" class="inline-img"/>

- You should now be able to navigate to each one of these pages as you click on their icons:

  



## Using`FlyoutMenuItem`

- Flyout Menu items are simply buttons added to the flyout menu to make certain functionality available everywhere throughout the app
- For example, I added a menu button to toggle between light mode and dark mode:

```xaml
 <MenuFlyoutItem Text="Switch Theme"  Clicked="Btn_SwitchTheme_Clicked"/>
```

- In the `AppShell.xaml.cs` code behind I defined the event handler:

```csharp
private void Btn_SwitchTheme_Clicked(object sender, EventArgs e)
{

    switch (App.Current.UserAppTheme)
    {
        default:
        case AppTheme.Light:
            App.Current.UserAppTheme = AppTheme.Dark;
            break;
        case AppTheme.Dark:
            App.Current.UserAppTheme = AppTheme.Light;
            break;

    }
}
```



## Customizing the `FlyoutMenu`:

- You can customize the `Header` and `Footer` of your MAUI app to your liking

<img src="{{site.baseurl}}/images/maui_navigation/flyoutmenu_customization.png" Height="100" class="inline-img"/>



- Let's try to add the `dotnet_bot.png` as the header and a horizontal stack layout containing this image and a label saying "I hope you are enjoying this!":

```xaml
    <Shell.FlyoutHeader>
        <!--Some code.. -->
    </Shell.FlyoutHeader>
    <Shell.FlyoutFooter>
        <!--Some code.. -->
    </Shell.FlyoutFooter>
```

<img src="{{site.baseurl}}/images/maui_navigation/flyout_with_header.png" Height="100" class="inline-img"/>



## Challenge (Easy): Microsoft's phases of the moon:

- Follow Microsoft .NET MAUI training module: https://learn.microsoft.com/en-us/training/modules/create-multi-page-apps/3-exercise-implement-flyout-navigation to create a flyout menu for their Astronomy app.

   

# Tab Bar navigation

The next navigation style we will learn about is Tab bar navigation:

- This is a permanent horizontal bar that appears generally on the bottom of the screen and holds various icons to navigate to some pages of the app.
- Warning! You might not necessarily need at Tab Bar, they increase the complexity of your app layout.



## Tab Bar Design Guidelines

- Microsoft's recommendations:

  > "Use tabs only for the pages that will be frequently used by the user" 
  >
  > "Use tabs only if your app has a few pages of equal importance"
  >
  > "Use 3-4 tabs to avoid over crowded apps"
  >
  > "Avoid using tab bars if your data is traversed from general to more specific"

- Apple's recommendations:

  > "Use tab bars to support navigation not provide actions"
  >
  > "Aim for a few tabs with short titles"
  >
  > "Keep tabs visible even when their content is unavailable". Otherwise your app's interface seems "unstable" (frustrates the user)



## Creating a simple`TabBar`

- To add a Tab bar simply use the `TabBar` object as a child of the `Shell`.

-  Then include `ShellContent` pages as children of the `TabBar`. 

  ```xaml
  <TabBar>
      <ShellContent
          Title="Home"
           Icon="home.png"
          ContentTemplate="{DataTemplate local:MainPage}"
          Route="MainPage" />
      <ShellContent
          Title="Search"
          Icon="search.png"
          ContentTemplate="{DataTemplate views:SearchPage}"/>
  
      <ShellContent
          Title="Videos"
          Icon="video.png"
          ContentTemplate="{DataTemplate views:VideosPage}"/>
      <ShellContent
          Title="Profile"
          Icon="user.png"
          ContentTemplate="{DataTemplate views:ProfilePage}"/>
  
  </TabBar>
  ```

  

### Implicit conversions	

- Note: MAUI actually wraps each `ShellContent` in a `Tab` object. But due to **implicit conversion** the hierarchy seems simplified. In this case:

   The real hierarchy is:

  - Shell
    - TabBar
      - Tab
        - ShellContent

  

  ## Adding sub pages

  

- You can add multiple `ShellContent` pages under the same `Tab` to create "grandchildren" pages

  ```xaml
      <TabBar>
          <ShellContent
          Title="Home"
           Icon="home.png"
          ContentTemplate="{DataTemplate local:MainPage}"
          Route="MainPage" />
          <ShellContent
              Title="Search"
              Icon="search.png"
              ContentTemplate="{DataTemplate views:SearchPage}"/>
          <Tab Icon="more.png" Title="New Post">
              <ShellContent
                  Title="Select photos"
                  Icon="select.png"
                  ContentTemplate="{DataTemplate views:FilePage}"/>
              <ShellContent
                  Title="Camera"
                  Icon="camera.png"
                  ContentTemplate="{DataTemplate views:NewPostPage}"/>
          </Tab>
          
          <ShellContent
              Title="Videos"
              Icon="video.png"
              ContentTemplate="{DataTemplate views:VideosPage}"/>
          <ShellContent
              Title="Profile"
              Icon="user.png"
              ContentTemplate="{DataTemplate views:ProfilePage}"/>
  
      </TabBar>
  ```

  

- This will result in having a hierarchical structure within your pages, in this case the `FilePage` and `NewPostPage` are grandchildren of the `TabBar`

   <img src="{{site.baseurl}}/images/maui_navigation/tabBar_2.png" Height="100" class="inline-img"/>
   
   

  

This is the current hierarchy 

`Shell`

- `TabBar`
  - `MainPage`
  - `SearchPage`
  - `Tab`
    - `FilePage`
    - `NewPostPage`
  - `VideosPage`
  - `Profile`

**Note**: I am omitting the `Tabs` added implicitly by the Shell on each `ContentPage`

## Combining `TabBar` and `FlyoutMenu`

- The `Shell` can only contain either a `FlyoutItem` object or a `TabBar` object.

  - If you wish to combine both you must make the `TabBar` a child of the `FlyoutItem`

- To combine the flyout menu and the tab bar, each `ShellContent` you wish to display in the `Flyout` should be wrapped within a `FlyoutItem` instead of the `TabBar` and keep the `ShellContent` you wish to keep in the Flyout as direct children of the `Shell`

  

```xaml
<FlyoutItem Title="Home" Icon="home.png">
    <ShellContent
        Title="Home"
         Icon="home.png"
        ContentTemplate="{DataTemplate local:MainPage}"
        Route="MainPage" />
    <ShellContent
        Title="Search"
        Icon="search.png"
        ContentTemplate="{DataTemplate views:SearchPage}"/>
    <Tab Icon="more.png" Title="New Post">
        <ShellContent
            Title="Select photos"
            Icon="select.png"
            ContentTemplate="{DataTemplate views:FilePage}"/>
        <ShellContent
            Title="Camera"
            Icon="camera.png"
            ContentTemplate="{DataTemplate views:NewPostPage}"/>
    </Tab>

    <ShellContent
        Title="Videos"
        Icon="video.png"
        ContentTemplate="{DataTemplate views:VideosPage}"/>
    <ShellContent
        Title="Profile"
        Icon="user.png"
        ContentTemplate="{DataTemplate views:ProfilePage}"/>

</FlyoutItem>


<ShellContent Title="Groups"
          Icon="group.png"
          ContentTemplate="{DataTemplate views:GroupsPage}"/>
<ShellContent Title="Info"
          Icon="info.png"
          ContentTemplate="{DataTemplate views:InfoPage}"/>
<ShellContent Title="Settings"
          Icon="setting.png"
          ContentTemplate="{DataTemplate views:Settings}"/>

<MenuFlyoutItem Text="Switch Theme"  Clicked="Btn_SwitchTheme_Clicked"/>
```

- This might be counter intuitive at first, but with XAML's implicit binding the children `ShellContent` are wrapped in `Tab`s then in a `TabBar`

The hierarchy is now: 



`Shell`

- `Flyout`

  - `TabBar`

    - `MainPage`

    - `SearchPage`
      - `Tab`
        - `FilePage`
        - `NewPostPage`

    - `VideosPage`

    - `Profile`

  - `GroupsPage`
  - `InfoPage`
  - `Settings`

**Note:** I am omitting the `Tabs` and the `FlyoutItems` implicitly added by the `Shell` 



## Challenge (Easy): Microsoft's Sunrise Page:

- Follow Microsoft .NET MAUI training module: https://learn.microsoft.com/en-us/training/modules/create-multi-page-apps/5-exercise-implement-tab-navigation



# Shell Navigation

So far we've seen how to access pages from the `TabBar` and the `FlyoutItem`, we have also seen how to `Push` a page into the stack and use the Back button to return to the previous page.

Shell navigation will enable us to navigate to any page using Uri links called routes. This type of navigation is especially useful if you wish to navigate to a particular page without having to visit the entire hierarchy of pages and return to the previous page without having to visit backwards all the pages on the navigation stack. 

 

## Routes

- Routes are Uris similar to a website's uri 
- They allow us to navigate through the hierarchy of the app.
- If you inspect the `ShellContent` of the `MainPage`, there is a set `Route` attribute.



```xaml
<ShellContent
    Title="Home"
    ContentTemplate="{DataTemplate local:MainPage}"
    Route="MainPage"/>
```

​	

- If the `MainPage` was at the **Root** of the app, you could navigate to this page using: 

```csharp
await Shell.Current.GoToAsync("//MainPage");
```

## Routes Registration in `XAML`

- Modify the `AppShell.xaml` to register routes for the following pages

```xaml
    <FlyoutItem Title="Home" Icon="home.png" Route="Home">
        <ShellContent ...
            ContentTemplate="{DataTemplate local:MainPage}"
            Route="MainPage" />
       
        <Tab Icon="more.png" Title="New Post" Route="AddPost">
            <ShellContent
                 <!--Some code.. -->
                Route="SelectFile"
                ContentTemplate="{DataTemplate views:FilePage}"/>
            <ShellContent
                 <!--Some code.. -->
                Route="NewPost"
                ContentTemplate="{DataTemplate views:NewPostPage}"/>
        </Tab>

    </FlyoutItem>

    <ShellContent Title="Groups"
               <!--Some code.. -->
              Route="GroupsPage"
              ContentTemplate="{DataTemplate views:GroupsPage}"/>
```



This creates the following hierarchy using the names of the pages as their routes:

"/"

- "Home"

   /"MainPage"

  /"SearchPage"

   /"AddPost"

  ​	 /"FilePage"

  ​	 /"NewPostPage"

  /"VideosPage"

  /"ProfilePage"

- "GroupsPage"

- "InfoPage"

- "Settings"

  

## Explicit routes Registration in `C#` 	

- Now, routes can get messy in complex hierarchies, just like for websites

- We want to avoid as much as possible magic strings in our app, to solve this:

  - Use the name of the page as its route

  - Use the `nameof()` method to register the route in the code behind

    

  In `AppShell.xaml.cs`:

  

  ```C#
  public AppShell()
  {
      InitializeComponent();
      
      Routing.RegisterRoute(nameof(MainPage), typeof(MainPage));
      /// Add the other pages...
      
  }
  ```

- **Note:** You may define hierarchical routes too at this point using forward slashes in the routes arguments, but for simplicity purposes we will use only the name of each file to route it.

  ```
   Routing.RegisterRoute($"//Home/{nameof(MainPage)}", typeof(MainPage));
  ```

  



## Performing Navigation using `Shell.Current.GoToAsync()`

- Let's add a `New Post` button inside the `GroupsPage` 

- Since the `NewPostPage` is part of the `TabBar`, you should use the **absolute route** to navigate to it (using "//"). Why? What happens if we don't use "//"

  ```csharp
  private async void Btn_AddPost_Clicked(object sender, EventArgs e)
  {
      await Shell.Current.GoToAsync($"//{nameof(NewPostPage)}");
  }
  ```



### Challenge (Easy): 

- I have disabled the Tab Bar inside the the `NewPagePage`:

  ```xaml
  <ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
               xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
               x:Class="DemoNavigation2.Views.NewPostPage"
               BackgroundColor="Black"
               Shell.TabBarIsVisible="False"
               Title="New Post">
  </ContentPage>
  ```

- Include an "x" button **to cancel the operation of taking a picture** and use the event handler of this button to navigate to the main page
- In the event handler, navigate to the main page using absolute routing ("//") and using the `nameof()` method
- Refer to [Microsoft's documentation](https://learn.microsoft.com/en-us/dotnet/maui/fundamentals/shell/navigation?view=net-maui-8.0) for the various route formats.



### Challenge question (Medium):

What's the point of using routing to go to the `MainPage`?  Why not simply `PushAsync` the `MainPage`?



### Challenge (Medium): Navigating to CommentsPage:

- You'll notice that the `CommentPage` is not in the Tab Bar hierarchy 
- Previously (Lab1) we were simply using `PushAsync` to push a new `CommentsPage` everytime.
- Let's try to reuse the same page and simply navigate to it using `GoToAsync`
- Modify the event handlers in the `MainPage` and the `VideosPage` to navigate to this `CommentPage` 
  - Without passing arguments (only passing the route as argument to `GoToAsync()`)
  - With 1 simple argument: using the constructor `public CommentsPage(int userid)`



### Challenge (Easy): Using Backward navigation

- You'll notice that I disabled the `NavBar` and the `TabBar` in the `CommentPage`
- Modify the event handler inside the `CommentsPage` to return to the previous back (regardless of which page it is)
- Refer to [Microsoft's documentation](https://learn.microsoft.com/en-us/dotnet/maui/fundamentals/shell/navigation?view=net-maui-8.0) for the various route formats.





### Passing Arguments to page constructor using `GoToAsync`

Passing simple data types as `strings` or `int` can be done using string formatting

```csha
await Shell.Current.GoToAsync($"{nameof(MyPage)}?SimpleArgument={12345}")
```



To pass multiple arguments and complex objects you need to use a dictionary `Dictionary<string, object>`:

```csharp
await Shell.Current.GoToAsync(nameof(MyPage), true, new Dictionary<string, object> {
    {"Arg1", value1 },
    {"Arg2", value2},
    {"Arg3", value3}
});
```

