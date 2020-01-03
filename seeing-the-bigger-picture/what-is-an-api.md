---
description: The Application Programming Interface is your window into an application
---

# 2.2 What is an API?

#### APIs are for Programmers

Most people will use an application via its user interface; clicking on buttons, selecting items from drop-down menus or perhaps interacting directly with geometry on their screen.

What they won't know is that the developers behind many applications choose to expose certain parts of their source code, letting other programmers read, edit, create or delete certain elements in the program's database - its API.

#### In the Restaurant

A common analogy for APIs is how restaurants traditionally work. A waiter will present you with a menu; a fixed set of options you can choose from. This is analogous to the application's user interface. 

Accessing a program via its API means we can ditch the waiter and walk straight into the kitchen. Instead of choosing from a menu, we'll have access to every ingredient and every device in the kitchen. This gives us total control, allowing us to create completely custom orders.

There is a lot of power in this. No more struggling against user interfaces wishing for functionality that the developers hadn't built yet - you're a developer now! Just make sure you don't give yourself or others food poisoning...!

#### The Application Programming Interface

API stands for _application programming interface_. This is a special back door into an application, designed specifically for programmers - most popular applications will have an API of some kind.

APIs aren't applications, are not a file and they don't have a graphical user interface. However, there will be certain environments \(defined by the program\) where you can write code that can access the API. This might be a macro panel, a specific server address or, as in Dynamo's case, a special [Python Script node](../getting-started/using-dynamos-python-node.md).

Normally, everything that is achievable via the user interface can be driven programatically, but there might also be parts of the API that were only ever intended for software developers to access. Learning to drive an application programatically has a number of benefits, some of which may sound too good to be true:

* Automating repetitive routines that a user might carry out.
* Building automatic 'safety checks' into your information.
* Carrying out complex mathematical operations for machine learning or data analysis.
* Developing completely custom operations, allowing us to create new extended functionality that the program never had originally. 

#### Where Can I Find an API?

A quick search will bring up dozens of guides and formal documentation for popular APIs, such as:

* **Revit API**: [2019 Developer Guide](http://help.autodesk.com/view/RVT/2019/ENU/)
* **Autocad .NET API**: [Online Guidance](https://www.autodesk.com/autodesk-university/class/Introduction-AutoCAD-Softwares-NET-API-Using-C-NET-2018)
* **Navisworks API**: [Navisworks Developer Center](https://www.autodesk.com/developer-network/platform-technologies/navisworks)

These guides are normally extensive, but are often aimed at experienced developers and might not always take the time to explain concepts that might slow down new programmers.

This guide has put together some introductory guidance for the Revit API, which can be read at the link below:

{% page-ref page="../4-revit-specific-topics/introduction-to-revits-api.md" %}

Dynamo also has an API, but if you're just starting out you''ll only need to know 1 or 2 things about it which will be covered in the [Getting Started](../getting-started/) chapter.   
  
For the curious, current documentation for Dynamo's API can be found [here](https://dynamods.github.io/DynamoAPI/).

