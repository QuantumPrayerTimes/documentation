---
title: What is QuantumPT ?
prev: /getting-started
next: /getting-started/screenshots
weight: 5
toc: true
---

{{% notice tip %}}
QuantumPT (QuantumPrayerTimes) is an application developped from scratch using **PyQt5** and **Python 3**.
{{% /notice %}}

___

### Why QuantumPT ?

This application is aimed to provide an offline **(without internet connexion)** prayer times calculator and reminders 
(Athans).

Multiple applications exist with the same purpose so why developing another one ?

{{% notice note %}}
I wanted to create a complete **free**, **open-source**, **fully portable** and **good looking** application.
{{% /notice %}}

Why 90% of the muslim desktop applications always looks like old application based on Windows XP (even Windows 2000) skin-like.
Fortunately, we have excellent mobile design applications for the same purposes.

I decided to take this project and improve the basic application with a good looking skin.
Of course, features are more important but why don't we combine **pretty design** with **awesome features** ?

___

### What are the features ?

The main features are :

1. [Various methods of time calculation](#1-various-methods-of-time-calculation)
2. [Supporting all locations around the world (using Internet or not)](#2-supporting-all-locations-around-the-world-using-internet-or-not)
3. [Local calculation of prayer times (no Internet is needed)](#3-local-calculation-of-prayer-times-no-internet-is-needed)
4. [Multiple time formats (12h/24h)](#4-multiple-time-formats-12h-24h)
5. [Real-time adjustment of minutes for each prayer times dynamically](#5-real-time-adjustment-of-minutes-for-each-prayer-times-dynamically)
6. [Multiple athans audio and Dua after athan](#6-multiple-athans-audio-and-dua-after-athan)
7. [Dua reminder with timer](#7-dua-reminder-with-timer)
8. [Entirely customized window and skin](#8-entirely-customized-window-and-skin)

___

##### 1 - Various methods of time calculation

There are different conventions for calculating prayer times.
The following table lists several well-known conventions currently in use in various regions:

| Method  | Description                                   |
| :-----  | :-----                                        |
| MWL     | Muslim World League                           |
| ISNA    | Islamic Society of North America              |
| Egypt   | Egyptian General Authority of Survey          |
| Makkah  | Umm al-Qura University                        |
| Karachi | University of Islamic Sciences, Karachi       |
| Tehran  | Institute of Geophysics, University of Tehran |
| Jafari  | Shia Ithna Ashari (Jafari)                    |

___

##### 2 - Supporting all locations around the world (using Internet or not)

Currently, the application is using the Internet connection to determine the Public IP address
that will be used to determine location using [Maximind GeoLite2](http://dev.maxmind.com/geoip/geoip2/geolite2) 
databases that translates the IP to a location.

If no Internet connection is available or location cannot be found, user can determine its location using local database.
This database has been taken from the [Socioeconomic Data and Applications Center (sedac)](http://sedac.ciesin.columbia.edu/data/set/grump-v1-settlement-points)
and a license is granted to use it and distribute it with the appplication.

{{% notice info %}}
I cannot verify all the cities or countries available in the database, if you don't find your city, or the coordinates are incorrect,
please [report it](https://quantumprayertimes.github.io/documentation/getting-started/getting-help/) and I will modify the database.
{{% /notice %}}

___

##### 3 - Local calculation of prayer times (no Internet is needed)

{{% notice tip %}}
Currently, the exactitude of the calculations on **some well-known cities** has been **verified**. 
{{% /notice %}}

Currently, the application uses the `Python` library : `PrayTimes` from http://praytimes.org

A slightly modified version is used for the application and is available in [Github](https://github.com/QuantumPrayerTimes/prayertimes)

The prayer calculation are computed according to the complete [detailed explanation](http://praytimes.org/calculation).
Some fixes and customizations have been added to fit the application needs.

{{% notice warning %}}
Please be careful and I advise each Muslim (including myself) to know the prayer times according to the sun and 
day times and not to always rely on calculations.
{{% /notice %}}

___

##### 4 - Multiple time formats (12h/24h)

This is as simple as choosing between [12h](https://en.wikipedia.org/wiki/12-hour_clock) or [24h](https://en.wikipedia.org/wiki/24-hour_clock) time format :
According to different place in the world, there are some norms and basics.

12h : e.g 5:35PM is used in USA

24h : e.g 17:35 is used in Europe

___

##### 5 - Real-time adjustment of minutes for each prayer times dynamically

When you use the program and your city has been determined, you may encounter some difference
between your local mosque prayer times and the program, this cannot be avoid since this is
calculation and it may vary according to locations.
 
If you want to ensure to repect and use the local mosque times, you can adjust the prayer times of the program to add an offset to match
the times wanted.

___

##### 6 - Multiple athans audio and Dua after athan

The application gives you the ability to choose between different athans and to preview the athans.

All of this is done dynamically by choosing the Athan. 

{{% notice info %}}
There is no possiblity to add
your own athans but it will be available very soon.
If you are a `Python` developer, you can add this feature from your side and share it.
{{% /notice %}}

___

##### 7 - Dua reminder with timer

There is a dua player that can be activated to run in background. This dua player will play
randomly some dua every minutes or 5 minutes according to the value you decide.
The duas are chosen randomly from a pre-defined directory.

{{% notice tip %}}
The application currently has 3 players that are `Athans`, `Dua` and `Athan preview`.
If athan is playing and it is also time for dua to play you don't want them to play at the same time.
Fortunately, there is a priority system that handles the priority as following :
**Athan > Dua > Preview**
{{% /notice %}}

___

##### 8 - Entirely customized window and skin

The application skin has been developed from scratch. The design is highly inspired from the [work](https://dribbble.com/shots/1841309-Prayer-Times-Widget-Setup)
of [Mohamed Yahia](https://dribbble.com/MohaStudio)
