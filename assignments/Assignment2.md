# Assignment 2: Email App milestone 2

* **Worth**: 10%
* 📅 **Due**: May 3rd, 2024 @ 23:59.
* 🕑 **Late Submissions**: Deductions for late submissions is 10%/day. 
  *To a maximum of 3 days. A a grade of 0% will be given after 3 days.*
* 📥**Submission**: Submit through GitHub classroom.



## Setup

- Installing EmailKit Nuget package
- Creating a dummy email address on outlook
- Enabling Pop and Imap 
- Disabling two factor authentication
- Send a few emails to this email address for testing purposes.



### Using MailKit 

- Documentation: https://github.com/jstedfast/MailKit/tree/master

- Subscribing to events in emails being changed: https://mimekit.net/docs/html/E_MailKit_MailFolder_CountChanged.htm

- Creating a MailService

- using imap client

- Create a CientConfig (email, password, port number, mail server)

  - Install MailKitSimplified 

  - Use Models.EmailReciverOptions with appsettings.json

  - Use MailReciever.MonitorFolder.SetIgnore...(...).SetMessageSummaryItems().OnMessageArrival()

    

- What's a mimemessage

- Parse a mimemessage into an email object used in the MauiEmail app

- Use Html body 

- change the Text Entry in the read page to html

- note that the Editor with forwarded emails will look ugly, but so long as the text is parse correctly.

- adding the concept of folders in the EmailRepo

- implement archive functionality

- implement delete functionality

## MVVM

- use mvvm?
- add unit testing?
- add email attachements?
- **add settings page to allow user to configure their email address, mail server provider, etc.**
- **include push notifications?**
- test on iOS?

### Unit tests
