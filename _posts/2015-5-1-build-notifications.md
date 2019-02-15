---
layout: post
title: Build Notifications: May 1, 2015
categories: Microsoft
tags:
  - Build
---

For the final day of Build, there was no keynote; we started immediately with sessions:

## What's New in C# 6 and Visual Basic 14
I focused on the primary language updates in C# 6 (not all features mentioned here):

- Introduction of the static using clause
- Getter-only auto-properties set from the constructor or directly on the properties
- Expression-bodied members
- Interpolated strings
- nameof
- Null-propagating operator as ?.
- Await in catch or finally blocks: one application would be logging something in your catch or finally block async
- Ability to filter exceptions

There was also a demo of how we can now use <a href="http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/support-for-debugging-lambda-expressions-with-visual-studio-2015.aspx">lambda statements in the Watch and Immediate windows</a>.

Under Tools > Extensions and Updates in Visual Studio 2015, there is a new package called <a href="https://visualstudiogallery.msdn.microsoft.com/a4445ad0-f97c-41f9-a148-eae225dcc8a5?SRC=VSIDE">C# Essentials</a>, which helps to give developers real-time tips and hints, as they are coding, on how C# 6 can make their coding life easier.

Curious about what is coming in C# 7? Stay current with the <a href="https://github.com/dotnet/roslyn/issues?q=label%3A%22Design+Notes%22+">design notes</a> from the Roslyn design meetings on <a href="https://github.com/dotnet/roslyn">GitHub</a>.

## Case Studies of HoloLens App Development
Organized as a series of case studies from different industries:

- NASA
    - <a href="http://drjeffnorris.com/">Jeff Norris</a> is the lead for mission operations innovation for the NASA Jet Propulsion Laboratory and discussed how they are working with Microsoft HoloLens to give people the ability to experience walking and being on Mars. He recalled how people literally teared up when they first experienced walking on Mars virtually. The applicability to planning routes on Mars for the Curiosity rover is also ground breaking. <a href="http://time.com/3839081/microsoft-hololens-mars-colony/">TIME</a> did a great overview of the new software NASA and Microsoft are teaming up on called OnSight, which allows NASA scientists to explore and interact with Mars through HoloLens.
- Trimble
    - Trimble discussed working with HoloLens to give architects the ability to build and review design plans in a physical space.
    - The transition from 2D documents to the 3D world is a game changer for the industry.
    - Check out the <a href="https://www.youtube.com/watch?v=kXVW4sUsh3A">Microsoft Partner Spotlight</a> for <a href="http://www.trimble.com/">Trimble</a> for more details.
- Cleveland Clinic and Case Western Reserve University
    - HoloLens is completely changing the health care field both educationally and professionally. Imagine learning surgeries through HoloLens, or interacting with a virtual heart.
    - <a href="http://www.case.edu/hololens/">Have a look</a> at how HoloLens is changing the health care industry.

## Building Consumer and Enterprise Device Solutions with Windows 10 IoT
- Gartner predicts that by 2017, 50 percent of Internet of Things solutions will originate in Startups that are less than three years old
- The Universal Windows Platform gives us the ability to take the same code base and deploy cross platform. This is the common theme of Build 2015 and was demonstrated with a simple Windows 10 universal weather app that was accessible on phone and then Raspberry Pi
- <a href="https://allseenalliance.org/developers">AllJoyn</a> was discussed as a framework to search for and communicate with other devices in the IoT landscape
- Securing IoT devices was discussed through Windows 10 IoT <a href="http://en.wikipedia.org/wiki/Trusted_Platform_Module">TPM</a>
- Have a look at <a href="http://www.windowsondevices.com/">Windows on Devices</a> for everything Windows IoT

Microsoft Build 2015 was fantastic!

I can’t thank Rightpoint enough for their supportive nature in providing opportunities for training for its employees and more personally, for the privilege of being invited to attend //build/ this year!

Jason Sears
