---
description: "Revit's API is large and so are its documents; learn to navigate them here \U0001F6F6"
---

# 4.2 How to Read Revit's API Documentation

#### Introduction

Although Autodesk's official documentation for the Revit API can be found as a .chm file in its SDK, the Revit API is best explored by visiting [APIDocs.co](https://apidocs.co/).

This site, created software developer [Gui Talarico](https://twitter.com/gtalarico), documents the APIs for Revit, Rhino, Grasshopper and more. Visit [APIDocs](https://apidocs.co/) to get a feel for reading API documentation; as a coder, this is what you'll be doing a lot.

#### Using APIDocs.Co

Since this website is such an invaluable resource to those wishing to become familiar with the Revit API, we've provided a brief guide to using the website.

![](../.gitbook/assets/apidocswebsiteannotated%20%281%29.jpg)

A typical workflow would involve making sure you've selected the appropriate version of the API for the product you're using \(on the left pane\) and then searching the API docs for the relevant subject matter you're concerned with. 

For instance, if looking to learn more about the FamilyInstance class, simply search for this in the search bar and select it from the autocomplete options. Details about this class will then appear in the details pane on the right. Further details to note about this pane \(as annotated in the image\):

1. This is the name of the page you're looking at. The Revit API has over 22,000 pages, although most of these you'll probably never need to look at!
2. This **&lt;&gt;** button will search several popular Github repositories for any code samples concerning this class. 
3. The 'Members' button will take you to an overall page displaying any methods, properties, interfaces or constructors for this class.

#### Jargon Time!

In order to read Revit's API docs, you'll need to be comfortable with some technical terminology. First of all, brush up on the terms we used here, such as classes and objects: 

{% page-ref page="../seeing-the-bigger-picture/object-oriented-programming.md" %}

Once you've got a handle on object-oriented programming terms, there are a few more terms it would be helpful to learn until you know them intuitively.

**Members**: ****A class' member page is just all of its methods, properties, etc collected together on a single page. This is extremely helpful if you're unsure whether a class has particular functionality or not.

**Methods:** Class methods are the functions it can run. These can be thought of like verbs - what can instances of this class '_do'_. For instance, objects of type [FamilyInstance](https://apidocs.co/apps/revit/2019/0d2231f8-91e6-794f-92ae-16aad8014b27.htm) have a flipHand\(\) method, letting you flip their handing.

```python
#Boilerplate code
my_family_instance.flipHand()
#This will flip an object of type familyinstance
```

Please Note: Any change made to the Revit document need to take place within an open transaction. Learn more about transactions [here](working-with-transactions.md).

**Properties**: Properties are more like the 'adjectives' of a class, helping you to understand more qualities about the specific objects \(i.e. instances\) of that class. For instance, the FamilyInstance class has a 'HandFlipped' property you can query, which will tell you if that particular instance has had its handing flipped.

```python
#Boilerplate code
is_it_handflipped = my_family_instance.HandFlipped
#This will return True or False depending on if its flipped!
```

**Constructors**

The constructors in the API are essentially telling you how to create instances of a class. For instance, the [XYZ class](https://apidocs.co/apps/revit/2019/b9b10e41-46c7-7e9b-bbd9-b6180e328d4d.htm) is used to define a point in Revit. We can use its constructors to create a new like so:

```python
#Boilerplate code
my_point = XYZ(0,0,0) #Creates a new point at the origin
#Note: Revit geometry isn't visible, unlike Dynamo geometry
```

**Enumerations**

Also known as enums, these are hard-coded lists which are generally intended to not change and to restrict choice to a set of options. An enumeration for traffic light states would look like:

1. Red
2. Flashing Orange
3. Steady Orange
4. Green

Therefore any traffic light object a user created would need to have its traffic light state set to one of the pre-written states as defined by the software vendors. You can select enum values like so:

```python
#Boilerplate code
traffic_light_value = TrafficLightState.FlashingOrange
#This will select one of the pre-defined states in our enum
```

Some of the key enumerations in the Revit API are:

* BuiltInCategory Enumeration: A list of every [BuiltInCategory](built-in-categories.md) in Revit
* BuiltInParameter Enumeration: A list of every [BuiltInParameter](built-in-categories.md) in Revit
* DisplayUnitType Enumeration: All of the [measurement units](working-with-units.md) Revit supports

{% hint style="info" %}
**Note: Version Changes**

The Revit API changes with each sub-release version. These are often minor changes made every few months. TheBuildingCoder blog does a great job of documenting the [changes made with each API version](https://thebuildingcoder.typepad.com/blog/2019/04/whats-new-in-the-revit-2020-api.html).
{% endhint %}

