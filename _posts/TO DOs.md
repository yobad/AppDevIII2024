# TO DOs

## UI

- Grid, VerticalStackLayout, HorizontalStackLayout, StackLayout, AbsoluteLayout --> DONE

- CollectionView (ListView)  
- ItemTemplate, DataTemplate
- ContentTemplate
- Controls: Buttons, sliders, entries



## Architecture

- Data Binding:
  - XAML to XAML Binding
  - XAML to Code Behind
- INotifyProperty
- MVVM



## Navigation

- Navigation logic can reside in a view's code-behind or a data-bound view-model. 
- Stack: PushAsync, PopAsync( see: https://www.telerik.com/blogs/beyond-basics-exploring-simple-navigation-net-maui)
- AppShell
- Routing
- Tab bar 
- Flyout
- `INavigationService` : A navigation service is typically invoked from view-models, this helps with testability. Note that this service is registered as a singleton with the dependency injection container inside the `MauiProgram.CreateMauiApp()`



## Deployment/Testing 

- Test on iOS

- Test on Mac

- How to determine the test plan

- Create unit tests

- How to test the View Model

  

## Dependency injection (Inversion of Control IoC pattern)

- https://learn.microsoft.com/en-us/dotnet/architecture/maui/dependency-injection
- Construction injection 
-  Other types (less common): property setter injection, method call injection
- the ViewModel recieves interfaces from various services, the VM doesn't have info about what is instantiating it.
  - for example the ViewModel might recieve an IServicePost interface without knowing the specifics of the various posts (video post, image post, text post)
  - This help us decouple the dependency between the ViewModel and the various kinds of social media post. Even if the image post is changed, this won't affect the VM.
  - Also this facilitates testability, we can mock a post and give it as argument to the post view model.
  - If new kinds of posts appear, we can easily add them and make them implement the IPost interface. Without modifying the viewModel.
  - Why IServicePost ? From the perspective of the View Model, it's using a service to fetch some kind of data, similar to a database service which fetches data regardless of whether the actual database is SQL or Oracle or NoSQL. 



## Integrating APIs and services

- local files, data can be saved:
  - **On device: Application Preferences**
  - **On device: File System**
  - **On device: Local Database**
  - Off-device: Cloud
  - Off-device: Webservices
- Embedded files
- databases 
- web services
- Using an API



## Authentication

- Firebase
- App Setting File ;
- Add the `appsettings.json` file to the Maui App as an `EmbeddedResource`. Here is an example:
  - The setting file has following values:
    - `RefreshRate` which is an integer.
    - `APIKey` which is a string.
    - `FireBase_DB_BaseUrl` which is a string.
    - `IsEnabled` which is a boolean.
- Conditional view based on user profile.





## Labs

- Lab0 - Getting Started:
  - MAUI project creation
  - Familiarity with Project Explorer
  - Hot reload 
  - Create Android Emulator
  - How to debug on Windows and on Android Emulator

- Lab 1 - Layouts (2%)
  - Utilizing the VerticalStackLayout and HorizontalStackLayout:
    - Understand how these layouts look like on mobile vs desktop
    - Spacing, Centering
  - Utilizing the Grid Layout:
    - Understanding auto vs fixed sizes
    - Positioning items on layout
    - playing with the width 
  - Utilizing the Absolute Layout:
    - Understanding what absolute vs proportional is
    - Understanding how to position, size items with absolute/proportional variables
  - Utilizing Flexible Layout:
    - How this fixes the Mobile/Desktop problem

- DemoDataBinding:

  - Create a simple page with text and slider, rotate the text with the slider
  - Increase the font with the slider
  - Create a post model (numlikes, comments = string[], username, uri )
  - Bind the model to the post page (image, username, likes, number of comments)
  - How can we bind the list to the comment section, we need as many placeholders as there are comments
  - Use of collectionview ...
  - Introduce CollectionView
  - DataTemplate
  - What happens if the number of comments changed?
  - ObservableCollection

- Lab 2 - Data Binding and CollectionView  (2%)

  - Slider to binding to label text
  - Creating a model and binding to UI 
  - *Utilizing the collection view*
  - *Start with static items with DataTemplate*
  - *Create an object to hold these items*
  - *Create a list of these objects*
  - Use Observable collection

- Assignment 1: 

  - Email inbox (Use of collectionView and email content, Reply, Send message View, create model email(title,body,recipient))
  - Online shopping app UI and model (no database connexion)
  - Choose a messaging app of your choice and create the View and the Model 

- Lab 3 - INotifyProperty 

  