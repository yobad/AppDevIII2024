---
layout: post
title: "Lab 3 - Saving data"
permalink: /labs/lab3
categories: labs
---

This lab will help you get familiar with the various MAUI layouts and controls. 

- 📝 **Worth:** 1%  (/5pts)
- 📅 **Due:** Friday March 22, 2024 @End of class
- 🕑 **Late submissions:** No late submission accepted.
- 📥 **Submission:** In class 



## Objectives

- Learn how to use application preferences
- Learn how to use embedded text files
- Learn how to use embedded app settings in a json format
- Learn how to use an API to save images on the cloud.



## Setup

- Clone the following app: https://github.com/AppDevIII-W24-Code/Demos/tree/main/MauiSocial

- Save it on your local drive `C:/Users/<studentId>`, not on One Drive

- Avoid lengthy file directories

  

#### Target platform

For this lab we will be testing the app on two different form factors:

- Android Emulator: Pixel 5 - API 34

- (optional) iOS : note I did not configure app entitlements for iOS nor did I test the app on this platform.

  

## Setup

1. From Demos folder, clone the MauiSocial 
2. Save it locally on your device (C: drive not on OneDrive)
3. I have already installed the important packages :
   - MediaKit (to save photos in the gallery)
   - Cloudinary (to upload pictures on the cloud)



## Exercise 1 (1 pt) - App Preferences

For this first exercise, you will have to complete the `Settings.xaml` page functionality in order to save three user preferences and then use them to define the Username displayed in `ProfilePage.xaml` and set the `App.Current.UserAppTheme`:

| Preference name | Type     |
| --------------- | -------- |
| "`username`"    | `string` |
| `"profileuri"`  | `string` |
| `"apptheme"`    | `bool`   |

**Setting preferences**

1. Inspect the `Settings.xaml` file and note the `TableView`'s content, these are the entries where the user can set their preferences.
2. In `Settings.xaml.cs`, implement the event handlers to set each of the preference listed above

> To set a preference use `Preferences.Set("nameofthepreference", value);`

3. For the `AppTheme` inspect the `MenuFlyoutItem` and its event handler added to the `AppShell.xaml.cs` to know how to get the current app theme.
4. In addition to saving the new preference, you should set the app theme to Light if the toggle is on, and set it to Dark if the toggle is off.

**Using preferences**

3. Restart the app to test the next few steps
4. Inside the `Settings.xaml.cs` page constructor, get the preferences saved to set the entries text and the toggle switch state. 

> To get a preference use
>
> `Preferences.Get("nameofthepreference", defaultvalue);`

5. Get the preference of the theme to set the App theme inside the `AppShell.xaml.cs`
6. Get the preference of the username and the user profile to set the username and profile picture inside the `ProfilePage.xaml.cs` and inside the `CommentsPage.xaml.cs`

 **✨ Test yourself question:** Is it possible to serialize an object inside the Preferences?

## Exercise 2 (1pt) - Reading an embedded file

1. Open the `InfoPage.xaml`and inspect the UI elements

2. This page will serve as a placeholder for a static text contained in the `Files/InfoText.txt` file

3. Open your `MSBuild` file and add the file as an `EmbeddedResource`

   

4. Implement the private method `LoadFile()`, open the embedded file and 

   > Hint: Use the `Assembly.GetExecutingAssembly().GetManifestResourceNames()` and `GetManifestResourceStream()` methods.	

5. Using a `StreamReader`, read the content of the file

6. Set the `FileEditor.Text` to the content of the file.

7. Display its content in the Editor

 **✨ Test yourself question:**   What other files are included as embdedded files? 



## Exercise 3 (1pt)

1. In the `PostPage.xaml.cs`, implement the `Btn_Save_Clicked()` eventhandler
2. Save the photo to the `FileSystem.AppDataDirectory`:

> Hint: Read the stream of the file and use `sourceStream.CopyToAsync(destinationStream);` 

3. You'll notice that you do not have access to this directory on the Android Emulator 
4. To validate that the file was correctly saved, we will upload the image on Cloudinary in **Exercise 5**. 



***Cloudinary***

*Cloudinary* is a a cloud management service for images and videos which allows programmatical uploads of media files and enables image and video transformations (cropping, filtered, etc). We will use the free license in order to upload pictures taken with the ***MauiSocial App***. 

Before using the service, we need to generate some api keys and secrets:

1. Create an [account](https://cloudinary.com/users/register_free) or use GitHub to login

2. Verify your account 

3. Go to the **Dashboard**

4. Get the **Cloud name**, **API Key**, **API Secret** 

5. Save them to an `"appsettings.json"` file inside your project directory.

   ```json
   {
     "CloudinaryConfig": {
       "cloudName": "1234",
       "apiKey": "1234",
       "apiSecret": "1234"
     }
   }
   ```

   

6. If you push your source code somewhere, do not push this `"appsettings.json"` file at the root of the project as these are your confidential keys.

   

## Exercise 4 (1pt) - Adding Configs from appsettings.json

1. Add the `"appsettings.json"` as an the embedded resources 

2. Install the following packages:

   - Install the `Nuget Microsoft.Extensions.Configuration.Json` 
   - Install the `Nuget Microsoft.Extensions.Configuration.Binder`

   I've already created a Services folder in which I included a Config class to parse the content of the json

3. Complete the constructor of the `CloudinaryService`:

4. Get the `"appsettings.json"` stream and use the following line to parse the config:

   ```csharp
   _config = configuration.GetSection(nameof(CloudinaryConfig)).Get<CloudinaryConfig>();
   ```

5. Now inside the constructor instanciate the API class:

   ```csharp
   Account account = new Account( _config.CloudName, _config.ApiKey, _config.ApiSecret );
   _cloudinary = new Cloudinary( account );
   ```

6. Use a `try/catch` inside the Service to ensure that the embedded file is properly found, parsed and used. 
7. To test it out, go to your `App.xaml.cs` and create a static instance of this class.
8. Run the app and observe any except being thrown. 

 **✨ Test yourself question:**  What's is the `"appsettings.json"` file typically used for? 

 **✨ Test yourself question:** What's the interest of including it as an embedded file. 



## Exercice 5 (1pt) - Upload an image



Using *Cloudinary*

1. Implement the method which should call `_cloudinary.UploadAsync()`:

   ```csharp
   public async Task<ImageUploadResult> UploadImage(string imageFilePath,string imageName)
   ```

2. Call the method inside the `Btn_Save_Clicked()` event handler inside the `PostPage`



## Bonus exercise 1pt  

James Montemagno created an [Plug-in](https://github.com/jamesmontemagno/MediaPlugin) which you can install as a Nuget package which facilitates the action of taking pictures, saving them and saving them to Gallery. 

Create a user preference inside the settings page which allow the user to choose weather they want to automatically save posts to their Gallery. Then modify the Save button event handler in the Post Page to save the photo to the Gallery using the Plug-in.



# References

1. [How To Upload Image(Cloudinary/Asp.Net Core)](https://medium.com/@karakizleyligul/how-to-upload-image-cloudinary-asp-net-core-e47023ff2431), [Karakiz Leyligul](https://medium.com/@karakizleyligul?source=post_page-----e47023ff2431--------------------------------), 2022, March 31. Last Access: 2024, March 20.

2. [Dot Net MAUI Configuration](https://github.com/jamesmontemagno/dotnet-maui-configuration/tree/master), [James Montemagno](https://github.com/jamesmontemagno), 2022, March 25. Last Access: 2024, March 20.

   