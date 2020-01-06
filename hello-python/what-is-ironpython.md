---
description: IronPython is simply a dialect of the Python language
---

# 1.3 What is IronPython?

#### Programming Languages Have 'Dialects'

Programming languages are general purpose, but they're always deployed for a specific task; perhaps you're building a website's UI or administering hundreds of databases. This context will always determine what functionality is and isn't important for any given task.  
  
Sometimes, a particular 'dialect' of a programming language is spun-off, to better cater for a specific technical requirement. Much like a human dialect, these spin-off languages use same terminology and grammar, but have been adapted slightly to extend certain features or to better-suit their intended context.

{% hint style="info" %}
These 'dialects' are known as **implementations** of a programming language. 
{% endhint %}

Python has several popular implementations which have been built for specific purposes: IronPython is the implementation of the Python language that Dynamo uses.

#### IronPython Targets the .NET Framework

IronPython was specifically designed to target libraries of the .NET framework \(See: [What is the .NET Framework?](../seeing-the-bigger-picture/what-is-the-.net-framework.md)\). This is very useful as it gives us access to Microsoft's .NET libraries, which are powerful and flexible resources built for professional software developers. A .NET Framework-capable Python implementation \(i.e IronPython\) was also needed to talk to the broader Autodesk AEC ecosystem which has API access via C\#

The trade-off is that IronPython is an open-source project, whose updates are not tied to the main Python project. Its development has lagged behind Python, meaning it lacks some of the newer features of the standard Python language.   
  
Furthermore, certain popular Python libraries \(such as numpy\) were never built to target IronPython and so cannot be used within Dynamo.   
  
Finally, it is worth noting that IronPython is almost identical to Python 2 and Python 3, so the knowledge you gain from using IronPython will be directly transferable to many other areas of development outside of Dynamo.

