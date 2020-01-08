---
description: OOP is a widely-adopted programming paradigm
---

# 2.4 Object-Oriented Programming

#### Introduction to OOP

Since we are dealing with software, we have to understand a little bit about how software gets written. There are multiple approaches out there \(such as procedural programming, functional programming\) that this guide won't go into.

Object-oriented programming \(referred to as OOP\) is a very popular programming paradigm that has been widely-used in software development for decades. It consists of the user defining abstract **'Classes'** in their code, which have various properties and abilities. These classes are meant to represent specific things in real life, perhaps a car or a person's bank account.

Once the necessary classes for the task have been defined, the programmer then  creates usable instances of them, known as **'Objects'**.

{% hint style="info" %}
This is very much how Family creation works in Revit; users first define an abstract family \(.rfa file\) and then go about placing instances of it in their model.
{% endhint %}

In a nutshell, OOP is an approach to building software that revolves around defining classes and the rules for the kinds of interactions their objects might have. In order to use Python in Dynamo, you'll just need to understand this key takeaway: 

* **Classes** are abstract definitions, like .rfa files. They live in a bubble.
* **Objects** are instances of these classes. Like placed Family Instances, they can interact with other objects.

#### Footnote: Classes are Data Types

Confident Dynamo users will already be familiar with manipulating the main basic datatypes: _strings, integers, floats and Booleans_. While these datatypes will appear in all kinds of software, each application will have its own custom datatypes as well - these are its classes.

If you use a Dynamo node to fetch a Revit document's active view, it won't be of a Boolean or an int type; it will be of a **View** type \(actually, it's long name is _Autodesk.Revit.DB.View_ and you can test this using the Object.Type node\).

