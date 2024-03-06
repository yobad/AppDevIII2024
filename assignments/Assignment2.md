# Assignment 1: Email App milestone 1

* **Worth**: 10%
* 📅 **Due**: March 18, 2024 @ 23:59.
* 🕑 **Late Submissions**: Deductions for late submissions is 10%/day. 
  *To a maximum of 3 days. A a grade of 0% will be given after 3 days.*
* 📥**Submission**: Submit through GitHub classroom.



## Project Preparation

- Check the `GitHub` classroom link shared with you on your section's Teams channel and accept the assignment.
- Once your private repo is created, clone it to your computer.
- The repo should contain a  `.NET MAUI App`  starter code using .NET Core 7.0
- Create a new `.NET MAUI App` project in the cloned folder using the following specifications:
- Organize your Views inside a folder **Views**
- Organize your C# classes inside a folder named **Models**
- Organize your static classes inside a folder named **DataRepos**
- Organize your services inside a folder named **Services**



## Objective

In this first assignment, you are tasked with creating a simple Email Client App offering various functionality. This is first milestone of the assignment, you will have to create the various views and models used by you app. The app will not be fully functional but will provide a starting point for the following assignment. 

- Design a mockup Email app using the .NET MAUI framework
- Design and implement various views using `CollectionView`
- Use shell navigation 
- Create models 
- Use data binding 
- (optional) Use converters
- (optional) Use templated views



## User Needs

The Email app must:

- Display multiple views showing the list of emails 

- Allow the user to switch between various views (Inbox, Archive, Sent, Bin)

- Offer a search function to search through the emails titles, contents and senders.

- Differentiate visually between Read/Unread emails 

- Differentiate visually between favorite/ non-favorite emails

- Offer a swipe function to archive, highlight (favorite), delete emails

- Offer tap functionality to display a detail view of the email

- Offer a functionality to write emails

  

**You do NOT have to implement:**

- Authentication of a user
- Connection to a mail server
- Send/Receive emails from a server

> To mockup data use a static `DataRepo`



## User stories

In a separate word document, PDF or markdown file 

- Write at least 5 simple user stories to translate the user needs above
- The title of your user stories should follow the format: *As a user, I ...*
- Each user story should be accompanied with an **acceptance criteria**



## UI Design 

1. Create **at least** the following pages:

   - `InboxPage`  (which will display emails in the inbox)
   -  `BinPage` (displays the deleted emails)
   -  `ArchivePage` (displays the archived emails)
   - `SentPage` (which will display all sent emails)

2. You should use a `CollectionView` of a collection of email items

3. In the Inbox view, you should include an `Entry` and a search button, this will serve as a search bar to filter out emails

   

### Model Classes

Organize the following software requirements and related them to the user stories you have created

1. Create an `Email` model with the following specifications:
   - Implements the `INotifyPropertyChanged`from **`System.ComponentModel`**
     - Implement the event `PropertyChanged`
     - Install the NuGet package ***PropertyChanged.Fody*** which will auto generate notification on property changes
   - encapsulates all concepts that are typically part of an email:
     - Sender Mail Address
     - Recipients Mail Addresses
     - Date and Time 
     - Subject
     - Body
     - Various states: IsRead, IsFavorite, IsArchived

> Hint: The email addresses should be valid, I suggest you use the class System.Net.Mail.MailAddress as a type for your email attibutes

1. Create an `EmailAccount` model with the following attributes:

   - First Name
   - Last Name
   - ProfilePic 	

   

   

## Additional notes

- I suggest you draw a quick wireframe of your app to help you define the views and their interactions with the model
- For all image button icons, download them from [flaticon](https://www.flaticon.com/) or [icon8](https://icons8.com/icons/set/library) 
- Create your layouts with hard coded data for simplification 
- Keep your code behind clean! (As little logic as possible)



## Grading Rubric

| Evaluation Criteria  | Details                                                      | Worth |
| -------------------- | ------------------------------------------------------------ | ----- |
| **UI Design**        | All requested elements available.<br /><br />Use of at least a Tab Bar or a Flyout menu.<br />Use of at least 1 `CollectionView`.<br />Use of application resources for UI styling.<br /> |       |
| **Model Classes**    | Proper class design and use of OOP pillars.<br />`Email` class <br /> `EmailAccount` |       |
| **User stories**     | User stories are written from the perspective of the end user. User stories are simple and concise. Every user story has a clear acceptance criteria. |       |
| **Functionality**    | App does everything and works as expected.<br />App does not crash. |       |
| **App Architecture** | Use of data repos for static data                            |       |
| **Coding Style**     | Use of comments.<br />Use of naming conventions.<br />Avoid the use of magic numbers: define constants when needed. |       |
| **Name & ID**        | At the top of all submitted files: provide your name, student ID and assignment number. |       |

