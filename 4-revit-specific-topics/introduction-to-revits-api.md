---
description: Revit's API has been developed over nearly two decades; let's get to know it!
---

# 4.1 Introduction to Revit's API

#### Introduction to Revit's API

Revit has had an accessible API since the early 2000s, which can be used to drive nearly every aspect of the software. As the Revit application is very complex and built to suit multiple audiences \(structure, MEP etc\) it is no surprise that its API is very large and takes a while to grasp intuitively.

#### Versions and History

With every release and sub-release of Revit, the Autodesk team makes minor updates or additions to its API. These changes mostly relate to functional changes within the software itself \(e.g. the recent egress analysis API\).

{% hint style="info" %}
This long history sometimes means that the Revit API can seem inconsistent or structured in unexpected ways - this often happens with older APIs, which cannot change without affecting lots of people.
{% endhint %}

#### The Structure of Revit's API

Given its size, it can help to take a step back and understand how this API is generally structured. The Revit API exposes around 1700 classes, 50 interfaces and 500 enumerations which cover almost every aspect and function of the application. The classes are subdivided between several namespaces, often relating to a specific usage \(e.g. plumbing or structural steel\). The vast majority of classes reside in the Autodesk.Revit.DB namespace.

On your machine, the API classes are split between two .dll files: _RevitAPI.dll_ and _RevitAPIUI.dll_ ****which can be found at: C:\Program Files\Autodesk\Revit \[Version\]

#### The Revit SDK & API Documentation

Software Development Kit \(SDKs\) are a common way for software vendors to distribute information about their APIs to developers. The official Revit SDK can be found [here](https://knowledge.autodesk.com/support/revit-products/learn-explore/caas/CloudHelp/cloudhelp/2019/ENU/Revit-Customize/files/GUID-D7E8694D-7DB3-41CA-A0F3-AF64DC2DA015-htm.html).

All [APIs](how-to-read-revits-api-docs.md) need technical documentation so programmers can pick them up and learn how to drive the application using code. The Revit SDK contains both official API documentation  in a .chm file as well as code examples \(written in Visual Basic and C\#\).

However, this guide recommends reading the Revit API in the [APIDocs.co](https://apidocs.co/) website, which is far more convenient than opening a .chm file. Make sure to bookmark it and find our guide to using the site here:

{% page-ref page="how-to-read-revits-api-docs.md" %}

This page also contains a quick guide to help explain some of the key terms you'll find in Revit's API documentation. Make sure to check it out!

#### Revit API Resources

Autodesk has many resources for getting acquainted with Revit's API, although many of these give examples in C\# rather than Python.

* Written by Jeremy Tammik, [TheBuildingCoder](http://thebuildingcoder.typepad.com/) blog is a prolific, detailed guide to all aspect's of Revit's API. Examples are mostly in C\#, but he does a great job explaining the API's intended functionality and use in everyday workflows.
* Danny Bentley has created [several helpful Youtube playlists](https://www.youtube.com/channel/UC1Dx-jGyRbvvHzZ8ZyGWF5w/playlists), demonstrating how to use Revit's API in both Python and C\#
* Gui Talarico \(who created APIDocs.co\) has collected together a [series of Revit Python resources](https://github.com/gtalarico/python-revit-resources) on his Github.
* Sol Amour, of Autodesk, has curated a series of [plug-and-play IronPython scripts for Dynamo](https://github.com/Amoursol/dynamoPython).

