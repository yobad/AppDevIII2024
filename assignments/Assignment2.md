---
layout: post
title: "Assignment 1 - Email App Notifications"
permalink: /assignments/assignment2
categories: assignments
---

* **Worth**: 5%
* 📅 **Due**: May 15, @11:59PM.
* 🕑 **Late Submissions**: Deductions for late submissions is 10%/day. 
  *To a maximum of 3 days. A a grade of 0% will be given after 3 days.*
* 📥**Submission**: Submit through GitHub classroom.



This Assignment, will be completed in class as the last lab of the course. We will complete some of the functionality of the MauiEmail app. 

### Objectives:

- Create a Mail Service which connect with a mailing server
- Download emails and send emails asynchronously by using `MailKit`
- Subscribe to a server-side event (new email received)
- Send push notifications by using `Plugin.LocalNotification`



## Setup

- For this assignment you may re-use your Assignment 1 code or use the starer code found **here**.
- Create a dummy email address on outlook:
  - Go to [Microsoft Outlook website](https://www.microsoft.com/en-us/microsoft-365/outlook/email-and-calendar-software-microsoft-outlook?rtc=1)
  - Click Create free account
  - Create a new email address
  - Create a new password that you can easily remember
  - Fill in the first name, last name (you can enter something like Mail Kit Test or something along this)
- Once logged in to your new email account:
  - Select **Settings**> **Mail**> **Sync email**.
  - Under POP and IMAP> Let other devices and apps use POP > make sure the toggle is on.
  - Make sure this option is checked: Let apps and devices delete messages from Outlook



## MailKit

[MailKit](https://github.com/jstedfast/MailKit) developed by [Jeffrey Stedfast](https://github.com/jstedfast) and is a cross-platform mail client library which uses [MimeKit](https://github.com/jstedfast/MimeKit). It offers authentication functionality as well as emailing functionality using POP3 protocol, Imap and Smtp. It is relatively easy to use for emailing. 

1. Install the Nuget Package: `MailKit` **version:** 4.3.0

2. Create a folder called `Config` 

3. Add a static class called `MailConfig` 

4. Add the following using:

   ```csharp
   using MailKit.Security;
   ```

5. Add the following public properties and set their values which are based on [Outlook's settings](https://support.microsoft.com/en-us/office/pop-imap-and-smtp-settings-for-outlook-com-d088b986-291d-42b8-9564-9c414e2aa040):

   - `Email`: the email address you just created
   - `Password`: the password you just created
   - `ImapHost`: **outlook.office365.com**
   - `ImapPort`: **993**
   - `ImapSocket`: `SecureSocketOptions.SslOnConnect`
   - `SmtpHost`: **smtp-mail.outlook.com**
   - `SmptPort`: **587**
   - `SmptSocket`: ` SecureSocketOptions.StartTls`

**Modification of the Email model**

6. Since the mail kit uses `MimeMessage` we need a way to convert them into our `Email` model.

7. Add a string property `Id` to the `Email` model:

   ```csharp
   public string Id { get; set; }
   ```

   

8. In your `Email` model add another constructor which takes a `MimeMessage` and a `MailKit.UniqueId` as parameter:

   ```csharp
   using MimeKit;// Add the following using
   
   namespace MauiEmail.Models
   {
       public class Email : INotifyPropertyChanged
       {
           // ...your Email model from Assignment 1
           public Email(MimeMessage mimeMessage, MailKit.UniqueId uniqueId)
           {
               this.Id = uniqueId.ToString();
               this.Date = mimeMessage.Date.DateTime;
               this.Subject = mimeMessage.Subject;
               this.Body = mimeMessage.HtmlBody;
               this.SenderAddress = new MailAddress(mimeMessage.From.ToArray()[0].ToString());
               this.RecipientAddress = new List<MailAddress>();
   
               // converting the InternetAddressesList to List of MailAddress
               mimeMessage.To.ToList().ForEach(
                   x => this.RecipientAddress.Add(new MailAddress(x.ToString())));
           }
   ```

8. Add a public method `ToMime()` :

   ```csharp
   
   public MimeMessage ToMime()
   {
       var message = new MimeMessage();
   
       message.From.Add(new MailboxAddress(SenderAddress.DisplayName, SenderAddress.Address.ToString()));
       foreach (var recipient in RecipientAddress)
       {
           message.To.Add(new MailboxAddress(recipient.DisplayName, recipient.Address.ToString()));
       }
   
       message.Subject = Subject;
   
       message.Body = new TextPart("plain")
       {
           Text = Body
       };
       return message;
   }
   ```

   



## MailService

1. Create a `Services` folder 

2. Create a class called `MailService` and add the following usings:

   ```csharp
   using MailKit;
   using MailKit.Net.Imap;
   using MailKit.Net.Smtp;
   ```

3. Which contain the following private fields:

   - `ImapClient imapClient` : This is a private instance of the `ImapClient` which uses the imap protocol to retrieve emails
   - `SmptClient smtpClient`: This is a private instance of the `SmptClient` which uses the imap protocol to retrieve emails

4. Create the following method which will connect and authenticate the Imap client: read [this](https://github.com/jstedfast/MailKit/tree/master?tab=readme-ov-file#using-imap) example to see how the client is authenticated synchronously. 

   

   ```csharp
   /// <summary>
   /// Method which connects imapClient if is is not already connected, and authenticates
   /// it if it's not already authenticated.
   /// </summary>
   public async Task StartImapAsync()
   {
       imapClient.ServerCertificateValidationCallback = (s, c, h, e) => true;
       /// Perform connect and authenticate...
   }
   ```

   > Notes: 
   >
   > - Call the `ServerCertificateValidationCallback = (...)` method before the connection to ensure that the server certificate validation is not checked, otherwise this might fail.
   > - There are async equivalents for each method `ConnectAsync()`, `AuthenticateAsync()`

5. Create the following method which will connect and authenticate the Smpt client: read [this](https://github.com/jstedfast/MailKit/tree/master?tab=readme-ov-file#sending-messages) example from MailKit. 

   ```csharp
   /// <summary>
   /// Method which connects smtpClient if is is not already connected, and authenticates
   /// it if it's not already authenticated.
   /// </summary>
   public async Task StartSmtpAsync()
   {
   	// To be completed...
   
   }
   ```

6. Create the following method, and a `try-catch` to catch any exception. return true 

   ```csharp
   /// <summary>
   /// starts the Smtp client, then sends an email asynchronously, and disconnects the client.
   /// </summary>
   /// <param name="email">Email to be sent</param>
   /// <returns>Task with boolean result for success of the operation</returns>
   public async Task<bool> SendMessageAsync(Email email)
   {
       try
       {
           await StartSmtpAsync();
           //...
   ```

   

7. To test the method, go to the `WritePage.xaml.cs` and modify the event handler to include this line:

   ```csharp
   await App.MailService.SendMessageAsync(EditEmail);
   ```

8. Test the operation of sending an email by sending an email to another inbox. 

9. Create the following method which connects the imap client, and downloads all the emails in the `Inbox`. Use [this](https://github.com/jstedfast/MailKit?tab=readme-ov-file#using-imap) example as reference. To make it easier for you, make this method synchronous and call it in the `EmailsRepo`. 

10. Test it out by sending a few emails to your newly created app. 

11. Show me your progress for today.

    

### Push Notifications

Coming in next...
