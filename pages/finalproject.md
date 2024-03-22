---
layout: page
title: Final Project
permalink: /project/
---

1. 📝**Worth**: 

   - **35%** (Connected Objects) 

   - **50%** (Application Development III)

2. 📅 **Due:** 7 milestones due dates across the months of April and May

3. 📥 **Submission:** Demos + Submission through GitHub

**Teachers:** Michael Haaf & Youmna Badawy

## Milestones - tentative dates

- #### [Milestone 1 - Combined (5%) March 25 - April 8](./milestone1)

- #### Milestone 2 - Connected Objects Apr 12 - 19

- #### Milestone 3 - App Dev III (10%) April 19 - 26

- #### Milestone 4 - Connected Objects April 26- May 3

- #### Milestone 5 - App Dev III (15%) May 3 - 10

- #### Milestone 6 - Connected Objects May 10 - 15

- #### Milestone 7 - Combined  May 15 - 21

  

## Introduction 

In this final capstone project you will integrate all the knowledge you have acquired in those courses and work in a team of 3 students on **designing and implementing a complete IoT solution for a fleet of container farms.** 

A **container farm** is a shipping container greenhouse. In other words, it is a stand-alone farming system for growing food inside a shipping container.

For more information on container farms and real-life examples, see the [context section](https://docs.google.com/document/d/1r5b5m1fvmDRZswrYxSoVx0ezlDFAbBRMkoZBTXbzJ6Y/edit#heading=h.c1waepqvlld1) further below.

# Context 

Your team has been hired as consultants by **JAC Corp** to help them design and implement a new IoT system which will be deployed inside their containers. JAC Corp wants to develop a stand-alone farming system for growing food inside a shipping container, which they call a **container farm.** 

This product is intended to be **rented out to clients** so that the client can grow food in any type of environment with a minimal amount of labour.

Below are some examples of where a container farm might be deployed:

- A high-end restaurant serving an exotic type of vegetable.
- A cruise ship offering fine fresh produce to their passengers.
- An agriculture school having a controlled growing environment for experimentation.
- A scientific mission in an extreme environment offering greens to the crew.
- A tech conference displaying a novel and inspiring attraction to visitors.
- An organisation improving food security in an unserved neighbourhood.

This system your team is responsible for, will include the sensors to monitor and control the containers as well as a mobile app which helps the users interact with the system. 

The container farm will be fully automated and can be remotely controlled by the client. A client still has to employ a **farm technician** who will manage the plants from inside the container.

A container farm will be a costly investment. JAC Corp is the **fleet owner**, and wants to monitor all container deployments **while they are rented out to clients** in order to guarantee a minimal level of care.

## Direct Competitors

There are currently a number of companies offering a similar product in the market.

- [Freight Farms](https://www.freightfarms.com/home/)
- [Grow Pod Solutions](https://www.growpodsolutions.com/shipping-container-greenhouses/)
- [Modular Farms Co](https://www.modularfarms.com.au/)
- [Growtainer](https://growtainers.com/)

# User needs

Your solution must allow the different users to view and control the different sensors and actuators based on their user role.

Below are the two primary users of the IoT system:

## Farm technician

The farm technician manages all plants inside the container from seed to harvest. They need to access the container and be able to safely lock it. They monitor and adjust the plant’s environment to assure optimal growth and to maximise the harvest. This user typically works inside the food container but will also monitor the growing conditions remotely. They are interested in making sure that the temperature, humidity and water levels are within normal range for their crop type. They are also interested in controlling the fans and lights inside the container. They must be able to access the container easily. 

## Fleet Owner

The fleet owner is responsible for overseeing all deployed container farms and have full access to the containers. They monitor the location of the containers, assure they are installed properly and keep track of any security issue. They want to use GPS localization, orientation information, vibration levels as well buzzer control. To ensure the security of their fleet, they want to be notified of suspicious activities based on motion and other metrics. This user monitors the containers from a remote location.

# Technical Requirements 

The IoT solution will use the following tech stack:

- reTerminal as the computing device (IoT "thing").
- Python as the on-device programming language.
- Microsoft Azure as the cloud infrastructure and IoT gateway.
- .NET and Maui for developing a user interface application for both Android and iOS

## Cloud Infrastructure

The container farm and the user application will connect using Azure infrastructure as illustrated below.

ADD IMAGE

The details of the connections and additional azure services are left for your team to design.



## A - Subsystems & Hardware

The container farm has 3 independent subsystems:



### 1. Plant subsystem

The plant subsystem is responsible for the monitoring and controlling of the growing environment.

| No   | Requirements                         |
| ---- | ------------------------------------ |
| A1.1 | To measure temperature and humidity. |
| A1.2 | To measure relative water levels.    |
| A1.3 | To measure soil moisture levels.     |
| A1.4 | To read fan state (on/off).          |
| A1.5 | To control fan state (on/off).       |
| A1.6 | To read light state (on/off)         |
| A1.7 | To control light state (on/off)      |



### 2. Geo-location subsystem

The geo-location subsystem is responsible for monitoring the transportation and placement of the container.

| No   | Requirements                      |
| ---- | --------------------------------- |
| A2.1 | To collect GPS location.          |
| A2.2 | To read pitch and roll angles.    |
| A2.3 | To read vibration levels.         |
| A2.4 | To read buzzer state (on/off).    |
| A2.5 | To control buzzer state (on/off). |

### 3. Security subsystem

The security subsystem is responsible for monitoring access and safety of the container.

| No   | Requirements                      |
| ---- | --------------------------------- |
| A3.1 | To collect GPS location.          |
| A3.2 | To read pitch and roll angles.    |
| A3.3 | To read vibration levels.         |
| A3.4 | To read buzzer state (on/off).    |
| A3.5 | To control buzzer state (on/off). |

## B - Mobile App

As shown in Figure 3, in the Cloud Infrastructure section, the mobile app represents the backend of the developed IoT solution. The objective is to provide access to the container farming operations via a mobile app. Below is a summary of of the general tasks or feature the app would provide: 



| No   | Requirements                                                 |
| ---- | ------------------------------------------------------------ |
| B1   | Provides a user authentication mechanism                     |
| B2   | Offers a Dashboard view of all farming operations and detail views of each component. |
| B3   | Allows remote control of all farming operations based on user profile. |
| B4   | Geolocation functionality:                                   |
| B4.1 | Displays real time location of a container                   |
| B4.2 | Displays real time orientation of a container                |
| B5   | Security functionality:                                      |
| B5.1 | Should allow real time monitoring of security related sensors |
| B5.2 | Should allow control of the security related sensors based on user authorization |
| B5.3 | Should display historical security highlights                |
| B6.  | Plant monitoring functionality:                              |
| B6.1 | Should display real time monitoring of environmental measures |
| B6.2 | Should allow access to various controls to adjust environment |
| B6.3 | Should display historical farming data for trend analysis    |
| B7   | User customization:                                          |
| B7.1 | Allows the user to set surveillance thresholds               |
| B7.2 | Allows the user to set notifications and alerts              |
| B8   | Data visualization:                                          |
| B8.1 | Displays data within graphs                                  |
| B8.2 | Displays data in an intuitive way                            |
| B8.3 | Compares real time data with user defined thresholds.        |
| B9   | Connectivity:                                                |
| B9.1 | Enable real time data access and control.                    |
| B9.2 | Robust mechanisms in case of network disruptions.            |



# Milestones

The project is organized in 7 sprints / milestones (tentative):

| **Sprint** | **Brief Description**                                        | **Dates**        | **Length** |
| ---------- | ------------------------------------------------------------ | ---------------- | ---------- |
| 1          | **Combined 5%**- Team contract finalised. (in a separate MD file)- User stories presented.- Wireframe for UI presented.- App design document. ([Details](https://arefmourtada.github.io/ADIII-W23/#/Project/Project_Milestone1)) - Access GitHub classroom and access your team repo, add Readme.md with that includes the information above. | Mar 25 to Apr 8  | 13 days    |
| 2          | **Connected Objects 9%**- Classes for using and controlling sensors and actuators.- Design OOP interface for hardware devices. | Apr 12 to 19     | 7 days     |
| 3          | **App Dev III 10%**- Maui App skeleton (pages design, navigation)- (optional) testing on iOS simulator- Models and repos are functional and tested | Apr 19 to 26     | 7 days     |
| 4          | **Connected Objects 7%**- Subsystems merged to work simultaneously.- Telemetry messages working (D2C).- Device twin desired properties working.- Finalise interface design for subsystem communication. | Apr 26 to May 3  | 7 days     |
| 5          | **App Dev III 15%**- Connect to the IoT Hub from the app- App should be able to handle multiple containers- Authentication service implemented and functional | May 3 to 10      | 7 days     |
| 6          | **Connected Objects 7%**<br>- All actuators can be controlled via the IoT Hub.<br>- Minimum of one Device Twin reported property working. | May 10 to May 15 | 7 days     |
| 7          | **App Dev III: 20%**- App controls IoT Hub settings.<br>- Display historical container data from Azure.<br>- Data visualizations.<br>-(optional) integration to database **Combined:**<br>- Presentations between Mar 15 and 21<br>- Final documentation. | May 15 to 21     | 6 days     |