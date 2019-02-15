---
layout: post
title: Build Notifications&#58; April 30, 2015
categories: Microsoft
tags:
  - Build
---

## Keynote
The keynote today dived deeper into the topics discussed yesterday organized around a series of conversations highlighted below.

Steve Guggenheimer was one of the speakers during the keynote – have a look at his <a href="http://blogs.msdn.com/b/stevengu/archive/2015/04/30/building-bridges-that-empower-developers.aspx">blog on the Keynote</a> for even more information.

- Media and Entertainment
    - <a href="https://www.muzikofficial.com/">Muzik Official</a> showed us the capability to drum without a drum set using low latency Bluetooth-enabled drumsticks. We also had a greeting from The Roots’ <a href="http://en.wikipedia.org/wiki/Questlove">QuestLove</a>.
- Commercial Apps
    - <a href="http://spark.autodesk.com/">Autodesk’s Spark Platform</a> will provider 3D printing capabilities to Windows 10
    - <a href="http://www.acumatica.com/">Acumatica</a> demonstrated new ways of reporting with Microsoft Power BI, showing the ability to translate drawings into search terms for querying
- Building for Windows 10
    - The Universal Windows Platform was discussed in more depth across all form factors: Mobile, Desktop, Xbox, Surface Hub, Holographic, IoT
    - The focus is around one design language and one control set. A great example of this is the new RelativePanel control which allows adaptability to different form factors through adaptive triggers (MinWindowWidth="600" for example)
    - Four divisions of development were discussed more fully today and how they can be bridged to the Universal Windows Platform:
        - Web
            - You can take existing websites, wrap them in universal apps, and make use of the new Windows 10 platform capabilities.
            - This discussion started with improvements coming with Microsoft Edge, such as the 4200+ interoperability improvements with the Microsoft EdgeHTML rendering engine.
            - Over 1.5 times faster than IE11 according to the <a href="http://browserbench.org/JetStream/">JetStream benchmark</a>; over twice as fast on the <a href="https://developers.google.com/octane/">Octane benchmark</a>
        - .NET & Win32
            - Ability to package WPF and Windows Forms apps into .appx and put them into the Windows Store
            - Ability to access universal windows APIs (live tiles, toast notifications)
            - Ability to use app services to pull in data from other universal apps into existing WPF and Windows Forms apps
        - Android Java/C++
            - Windows phones will include an Android subsystem and run these migrated apps in a secure container
            - Gives the ability to reuse the existing Java/C++ code but take advantage of the Windows 10 new platform capabilities
        - iOS Objective C
            - Use the same objective C code and use it with the Windows 10 new platform capabilities
            - You can convert XCode project files into visual studio solutions
            - Full support in visual studio with syntax highlighting
            - This is how King bought <a href="https://king.com/#!/play/candycrush">Candy Crush Saga</a> to the Windows Phone
- Cross Platform
    - Demos were given on the consumer side with Fitbit showing adaptable design between PC and Xbox as well as the commercial side with Siemens demoing the Microsoft Surface and the Surface Hub
    - Announced <a href="http://www.manifoldjs.com/">ManifoldJS</a>, which allows developers to create apps across all platforms from an existing website with a manifest.json file
- Data and the Intelligent Cloud
    - <a href="http://blogs.microsoft.com/blog/author/josephsirosh/">Joseph Sirosh</a> discussed machine learning. He perhaps said it best when he said “The Cloud is Eating Software.” What we have now is this notion of Data as a Platform - digesting data and producing intelligence.
    - He discussed this in conversations around retrospective analytics, real-time analytics, predictive analytics and intelligent SaaS apps.
    - An example of real-time analytics I thought was interesting was <a href="http://www.how-old.net/">How-Old.net</a>
        - Using the new <a href="http://www.projectoxford.ai/">Project Oxford Suite</a>, which includes intelligent services such as the <a href="http://gallery.azureml.net/MachineLearningAPI/b0b2598aa46c4f44a08af8891e415cc7">Face API</a>, How-Old.net is able to make educated guesses on my age and gender. Read more about it <a href="http://blogs.technet.com/b/machinelearning/archive/2015/04/29/fun-with-ml-stream-analytics-and-powerbi-observing-virality-in-real-time.aspx">here</a>.

## The Future of TypeScript: ECMAScript 6, Async/Await and Richer Libraries (Anders Hejlsberg)
- <a href="http://blogs.msdn.com/b/typescript/archive/2015/04/30/announcing-typescript-1-5-beta.aspx">TypeScript 1.5 Beta was released today</a>
- The presentation started with an overview of TypeScript: a typed superset of JavaScript that compiles to plain JavaScript
- One of the great aspects with TypeScript is the ability to use features from the future today. You may not be able to make use of ECMAScript 6 out of the box across all browsers and to avoid this, TypeScript allows us to use all of the facilities of ECMAScript 6 downgraded to run on ECMAScript 5 and earlier
- Anders reinforced TypeScript’s focus on "Any Browser. Any Host. Any OS" and how they have been open source from the beginning.
- One of the interesting features in TypeScript 1.5 is the <a href="https://github.com/Microsoft/TypeScript/wiki/tsconfig.json">tsconfig.json</a> file, which gives developers the ability to specify their appropriate flavor of ECMAScript (targeting 5 versus 6 for example)

## Building Rich, Contextually Aware Universal Windows Apps Using Sensors
- This session's focus was on contextually aware sensor APIs, which are available under the <a href="https://msdn.microsoft.com/library/windows.devices.sensors">Windows.Devices.Sensors</a> namespace. Here is a brief overview of a few:
- Proximity API: a typical application here is automatically turning off your phone's display during a phone call
- Activity Detection API: used to detect a user’s motion context, such as running, walking, in a vehicle, or stationary, among others. This can be applied to navigation and maps, as well as health and fitness tracking
- Pedometer API: used to detect a user’s steps both walking and running as well as the time spent walking and running. The most applicable use here is likely health and fitness tracking
- Barometer / Altimeter API: reports station pressure as well as relative altitude and elevation. With this API, imagine indoor navigation, like walking up an escalator and detecting the change in elevation. Weather forecasting is also obviously a typical application here
- If none of those fit your scenario, you can also develop a custom sensor using the Custom Sensor API. Some examples mentioned where a CO2 sensor, UV sensor or Heart Rate Sensor

## Entity Framework 7: Data for Web, Phone, Store, and Desktop
- The tag line for this release is: New Platforms / New Data Stores
- EF7 will be supported on ASP.NET 5 (both .NET 4.6 and Core), as well as with Universal Windows Applications across Windows, Mac and Linux
- New data stores will be provided, both relational and non-relational, such as Azure Table Storage, including an in-memory provider for testing purposes.
- A new core will be included with the same top-level experience as EF6.X. One of the interesting new features is the idea of pay-per-play components. EF7 will be more modular with SQL Server broken out into its own assembly, for instance: EntityFramework.SqlServer
- New Features:
    - Logging with instances implementing ILogger- ability to log all SQL queries executed against the database
    - SaveChanges Improvements - batching up multiple changes into a single round trip to the database
    - Shadow state - ability to have data expressed in your data store while not actually being represented in a CLR class. For instance, perhaps you want a LastUpdated DateTime for an object but you don't want to expose it in your class. You can create this from the DbContext in OnModelCreating. You can then override SaveChanges and use ChangeTracker to set the LastUpdated property.
- Learn more about EF7 <a href="http://aka.ms/aboutef7">here</a>.

Looking forward to tomorrow – especially the discussion on C# 6!

Jason Sears
