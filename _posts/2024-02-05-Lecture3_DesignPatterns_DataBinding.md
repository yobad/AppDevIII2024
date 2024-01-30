---
layout: post
title: "Lecture 4: MVVM"
permalink: /lectures/mvvm/
categories: notes
---

## MVVM

- Very popular architecture
- Creates a responsive binding between the View and the Model 
- Idea: UI should update the code behind and vice a versa without having to explicitly do it in the event handlers, etc.



Lab - use medal tracker:

- Provide students with start code collection view medals, swipe view on elements, delete elements, add country with flag and color, etc.
- Guide them through MVVM
  - Create CountryViewModel which inherits from INotifyPropertyChanged
  - raise OnPropertyChanged(GoldMedal), silverMedals, bronze, etc.
  - those values are already bound to View
  - show them how to install Nuget Package -> CommunityToolkit.MVVM
  - make CountryViewModel inherits from ObservableObject (templating all the observable properties)
    - [ObservableProperty] GoldMedal, SilverMedal, BronzeMedal.

Assignment idea:

- collection view of student github ids with search bar
- initially it's static, I can't add new ids
- 1. Add data binding to text entry (create view model: MainViewModel which implements INotifyPropretyChanged)
  2. implement the OnPropertyChanged, pass in variable