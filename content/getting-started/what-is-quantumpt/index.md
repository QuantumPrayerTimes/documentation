---
title: What is QuantumPT ?
prev: /getting-started
next: /getting-started/requirements
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
5. [Adjust minutes for each prayer times dynamically](#5-adjust-minutes-for-each-prayer-times-dynamically)
6. [Multiple athans audio and Dua after athan](#6-multiple-athans-audio-and-dua-after-athan)
7. [Dua reminder with timer](#7-dua-reminder-with-timer)
8. [Real-time adjusting prayer times](#8-real-time-adjusting-prayer-times)
9. [Entirely customized window and skin](#9-entirely-customized-window-and-skin)

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
that will be used to determine location using Maximind GeoLite2 databases that translates
the IP to a location : http://dev.maxmind.com/geoip/geoip2/geolite2

If not Internet location is found, user can determine its location using local database.
This database has been taken from and I possess a license to use it and distribute it into my program.
I cannot verify all the cities or countries available in the database, if you don't find your city,
please report it and I will add it to the database.

___

##### 3 - Local calculation of prayer times (no Internet is needed)

I am currently using the Python library : PrayTimes from http://praytimes.org.

The prayer calculation are computed according to the complete detailed explanation here :
http://praytimes.org/calculation
I added some fixes and customization to fit my application needs.

Currently, I did not verify the exactitude of the calculations. This work will be done in
the future, please be careful of this and I advise each Muslim beginning by me to know
the prayer times according to sun and day times and not to always rely on calculation.

___

##### 4 - Multiple time formats (12h/24h)

This is as simple as choosing between 12h or 24h time format :
According to different place in the world, there are some basics.

12h : e.g 5:35PM
24h : e.g 17:35PM

___

##### 5 - Adjust minutes for each prayer times dynamically

When you use the program and your city has been determined, you may encounter some difference
between your local mosque prayer times and the program, this cannot be avoid since this is
calculation and it may vary according to locations. if you want to ensure to repect and use
your mosque times, you can adjust the prayer times of the program to add an offset to match
the exact times.

___

##### 6 - Multiple athans audio and Dua after athan

The program gives you the ability to choose between different athans and to preview the athans.
All of this is done dynamically by choosing the Athan. There is currently no possiblity to add
your own athans but it will be available very soon, or if you are a Python expert you can add
this feature from your side and maybe share it with us ;)

___

##### 7 - Dua reminder with timer

There is a dua player that can be activated to run in background. This dua player will play
randomly some dua every minutes or 5 minutes according to the value you decide.
The duas are chosen randomly from a list.

The program currently has 3 players that are Athans, Dua and Athan preview.
If athan is playing and it is also time for dua to play you don't want them to play at the same time.
Fortunately, there is a priority system that handles the priority as following :

Athan > Dua > Preview

___

##### 8 - Real-time adjusting prayer times

___

##### 9 - Entirely customized window and skin

### Future developments

This part will be constantly updated.

Currently, and the most important thing is to add tests for each piece of code written. This may take some times but
it is important to test that every features is working when updating the code.

### Who are the authors ?
