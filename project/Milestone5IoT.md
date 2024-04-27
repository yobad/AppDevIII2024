---
layout: page
title: Milestone 5
permalink: /project/milestone5

---

📝**Worth**: 15%

📅 **Due:** May 13-14 in class Demo.

📥 **Submission:** Code pushed on Repo + Short demo in class:

Book your demo time here:

[Book time for Demo IoT Hub connection - Section 1 ](https://outlook.office365.com/bookwithme/user/be6f45e6ebc4491f8e1ec3d7917a39a0@johnabbott.qc.ca/meetingtype/QBBKtDHJ1kiKrye9KzmjpQ2?anonymous&ep=mcard)   

[Book time for Demo IoT Hub connection - Section 2 ](https://outlook.office365.com/bookwithme/user/be6f45e6ebc4491f8e1ec3d7917a39a0@johnabbott.qc.ca/meetingtype/6Q1L7C_31UW7Dka6wc3IQg2?anonymous&ep=mcard)



### Introduction

In milestone 3, you have laid the foundation of your app. You created your models and most of your views. In this milestone you will connect and retrieve data from the IoT Hub.

By the end of Milestone 5 your team should deliver the following:

- `.Net Maui` app connects to Azure IoT hub and retrieves data.
- Models updated as per the telemetry.
- Basic data displayed in views.
- The user authentication is implemented

> **Notes**
>
> - **The code organization statements stated below are suggestions to have a better and clean code.**
> - **Your code design could adapt the concepts as is or change them as needed.**

### Authentication 

In this milestone you Login page should be fully functional allowing a user to be authenticated. You do not have to implement a sign in page (this is a nice to have). 

You should also route the user according to who they are (owner or technician). You may simply save a local repo of users with their type. Implementing a database of users is a nice to have. 

Provide the user credentials in your README.md file to allow me to test your app. 

### Connection to Azure IoT Hub

You should start the process of connecting you app to `Azure IoT Hub`. The key objective in this step is to keep the **code as organized as possible**.

**Fixed Values**

- Any fixed data values such as *connection strings*, *server settings*, *credentials*, etc. should be be inside an `appsettings.json` file. You should have a `Config` or `Settings` class which helps deserialize the json. 
- This class (`Config` or `Settings`) should probably be static or instantiated in the `App` class, **so the values can be easily accessed through out the app.**
- Follow variable naming conventions in .NET
- Provide meaningful names.
- Use constants where applicable.

**Handling multiple containers**

- If you are planning for multiple Container-Farms, the instructions above might not be applicable to you, as you will have multiple connection strings, etc.
- In this case, create a model to track each container data (connection strings), if not already done.

**Use of Data Repositories**

- Retrieving data from the any source should be done through a data repository class. (similar to the databases lab)
- You app will eventually receive a single telemetry for all subsystems. Start planning for this as you design the repo.
- **Keep in mind OOP abstraction pillar: a single class should describe a single entity and should not include unrelated code.**

### Error handling

**Defensive Programming**: *is a form of defensive design intended to ensure the continuing function of a piece of software under unforeseen circumstances. ([Wikipedia](https://en.wikipedia.org/wiki/Defensive_programming))*

- As you are starting to interact with the cloud, remember that your app should be ready **to handle disruptions **
- Similar to the authentication lab, you should make sure that the user is notified of incorrect credentials and network disruptions. 
- Additionally, data retrieval is dependent on accessing the network. Make sure your code adds `try` and `catch` clauses where needed.
- Refer to [`Network Connectivity`](https://learn.microsoft.com/en-us/dotnet/maui/platform-integration/communication/networking?view=net-maui-7.0&tabs=android) documentation (and the lab on authentication) to check if the network is available before proceeding to connect to any network resource.

### Update of Data Models

In the current `Connected Objects` milestone, the telemetry payload is being well established and **clearly formed**. Revisit the `Models` created in the previous milestone and make any needed adjustments.

### Display of Data

Start the process of connecting the backend, the data, with the frontend user interface.

- Use the data repository classes you have created to retrieve the data.
- Use `Data Binding`to display the data into your views if you have not done already.
  - Display the basic data.
  - Include the units of measurements so that if is at least relevant.
  - Be mindful of real time updates, your views should be notified when the data is changing. 
  - You may start working on advanced views (if you have not already started).
- As you are not required to include information about the actuators in your message, any UI control that is supposed to send data back to the IoT hub is not required to function in this milestone.

### Code Quality & Comments

Refer to Milestone 3 for the details of [Code Quality](https://yobad.github.io/AppDevIII2024/project/milestone3#code-quality) and [Comments](https://yobad.github.io/AppDevIII2024/project/milestone3#comments-and-documentation).

## Grading Rubric (15 points)

Breakdown will be provided soon.

| Evaluation Criteria                                          | Worth                         |
| :----------------------------------------------------------- | :---------------------------- |
| Use of Repo Classes                                          | **1.5 points**                |
| Models Updates                                               | **0.5 point**                 |
| IoT Hub Connection - Service Classes                         | **2 points**                  |
| **Display of Data in Views** Live data retrieved from Azure IoT Hub and displayed in View Views organized | **3 points** 2 points 1 point |
| Code Quality & Comments                                      | **0.5 point**                 |
| **Teams meeting demo** Organized and prepared. Time: being there on time & respect time limit. | **2 points** 2 points 1 point |
| Action taken on comments from previous milestone             | **0.5 point**                 |



## Deliverables

- Schedule a meeting with me on Teams to demonstrate your progress. A booking link is provided via MIO.
- **All team members must attend the meeting.**
- Your presentation should not exceed 10 minutes.



## Grading Rubric (/10 points )

| Evaluation Criteria                                     | Worth         |
| :------------------------------------------------------ | :------------ |
| Action taken on comments from previous milestone        | **0.5         |
| **Repos**                                               | **2 points**  |
| Data retrieved within repos                             | 1 point       |
| Repos are updated as data changes                       | 0.5 point     |
| Models Updates                                          | **0.5 point** |
| **Services**                                            |               |
| Authentication                                          | 1 point       |
| IoT Hub Connection                                      | 3 points      |
| **Views**                                               | **3 points**  |
| Data retrieved from Azure IoT Hub and displayed in View | 2 points      |
| Views organized                                         | 1 point       |
| Live updates of the data within views                   | 1 point       |
| **Network disruption error handling**                   | **2 points**  |
| Network disruption at authentication is handled         | 1 point       |
| Network disruption during data retrieval is handled     | 1 point       |
| **Code Quality & Comments**                             | **0.5 point** |
| **Teams meeting demo**                                  | **2 points**  |
| Organized and prepared.                                 | 2 points      |
| Time: being there on time & respect time limit.         | 1             |
