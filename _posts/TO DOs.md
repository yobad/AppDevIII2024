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
- MVVM
- INotifyProperty



## Deployment 

- Test on iOS
- Test on Mac

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
  - Utilizing the collection view
  - Start with static items with DataTemplate
  - Create an object to hold these items
  - Create a list of these objects
  - Use Observable collection

- Assignment 1: 

  - Email inbox (Use of collectionView and email content, Reply, Send message View, create model email(title,body,recipient))
  - Online shopping app UI and model (no database connexion)
  - Choose a messaging app of your choice and create the View and the Model 

- Lab 3 - 

  