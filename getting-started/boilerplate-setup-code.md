---
description: Boilerplate code does all of the initial setup so you can start coding
---

# 3.2 Boilerplate Setup Code

#### Boilerplate Code Lives Up Top

It's important to understand what boilerplate code is as your scripts simply won't run without it! It's a part of the context we spoke about in the [Seeing The Bigger Picture](../seeing-the-bigger-picture/) section.

In almost any language, any script begins with bringing in all the libraries and resources you'll to load as part of your script. Most Dynamo definitions depend on loading in custom node packages and scripting is the same. The more generic term for this is **dependencies** and the copy/pasted code you'll use to bring these into your scripts is generally known as **boilerplate code**.

The libraries you bring into your script can come from a wide variety of sources - IronPython has the ability to load .NET Framework libraries, which cover everything from UI development to networking and highly capable. 

#### Gimme That Boilerplate Code

If you're simply looking for some quick copy/paste code that will work in most Python Script nodes, then this is provided for you below.

Please Note: **Not all of this is necessary.** While not absolutely vital, it very much helps to have an understanding of what each line does and why. If you'd like to learn more about each line, click the _Annotated Boilerplate Code_ tab below to switch to a fully-annotated version of the code.

{% tabs %}
{% tab title="Revit Boilerplate" %}
{% code title="RevitBoilerplate.py" %}
```python
import clr
import sys
sys.path.append('C:\Program Files (x86)\IronPython 2.7\Lib')
import System
from System import Array
from System.Collections.Generic import *
clr.AddReference('ProtoGeometry')
from Autodesk.DesignScript.Geometry import *
clr.AddReference("RevitNodes")
import Revit
clr.ImportExtensions(Revit.Elements)
clr.ImportExtensions(Revit.GeometryConversion)
clr.AddReference("RevitServices")
import RevitServices
from RevitServices.Persistence import DocumentManager 
from RevitServices.Transactions import TransactionManager 

clr.AddReference("RevitAPI")
clr.AddReference("RevitAPIUI")

import Autodesk 
from Autodesk.Revit.DB import *
from Autodesk.Revit.UI import *

doc = DocumentManager.Instance.CurrentDBDocument
uiapp = DocumentManager.Instance.CurrentUIApplication 
app = uiapp.Application 
uidoc = uiapp.ActiveUIDocument

#######OK NOW YOU CAN CODE########
```
{% endcode %}
{% endtab %}

{% tab title="Revit Boilerplate \(Annotated\)" %}
{% code title="RevitBoilerplateAnnotated.py" %}
```python
import clr #This is .NET's Common Language Runtime. It's an execution environment
#that is able to execute code from several different languages.
import sys #sys is a fundamental Python library - here, we're using it to load in
#the standard IronPython libraries
sys.path.append('C:\Program Files (x86)\IronPython 2.7\Lib') #Imports the
#standard IronPython libraries, which cover everything from servers and
#encryption through to regular expressions.
import System #The System namespace at the root of .NET
from System import Array #.NET class for handling array information
from System.Collections.Generic import * #Lets you handle generics. Revit's API
#sometimes wants hard-typed 'generic' lists, called ILists. If you don't need
#these you can delete this line.
clr.AddReference('ProtoGeometry')  #A Dynamo library for its proxy geometry
#classes. You'll only need this if you're interacting with geometry.
from Autodesk.DesignScript.Geometry import * #Loads everything in Dynamo's
#geometry library
clr.AddReference("RevitNodes") #Dynamo's nodes for Revit
import Revit #Loads in the Revit namespace in RevitNodes
clr.ImportExtensions(Revit.Elements) #More loading of Dynamo's Revit libraries
clr.ImportExtensions(Revit.GeometryConversion) #More loading of Dynamo's
#Revit libraries. You'll only need this if you're interacting with geometry.
clr.AddReference("RevitServices") #Dynamo's classes for handling Revit documents
import RevitServices 
from RevitServices.Persistence import DocumentManager #An internal Dynamo class
#that keeps track of the document that Dynamo is currently attached to
from RevitServices.Transactions import TransactionManager #A Dynamo class for
#opening and closing transactions to change the Revit document's database

clr.AddReference("RevitAPI") #Adding reference to Revit's API DLLs
clr.AddReference("RevitAPIUI") #Adding reference to Revit's API DLLs

import Autodesk #Loads the Autodesk namespace
from Autodesk.Revit.DB import * #Loading Revit's API classes
from Autodesk.Revit.UI import * #Loading Revit's API UI classes  

doc = DocumentManager.Instance.CurrentDBDocument #Finally, setting up handles to the active Revit document
uiapp = DocumentManager.Instance.CurrentUIApplication #Setting a handle to the active Revit UI document
app = uiapp.Application  #Setting a handle to the currently-open instance of the Revit application
uidoc = uiapp.ActiveUIDocument #Setting a handle to the currently-open instance of the Revit UI application

#######OK NOW YOU CAN CODE########
```
{% endcode %}
{% endtab %}
{% endtabs %}

**Python Script Templates**

In Dynamo 2.0, Python [script templates](https://primer.dynamobim.org/10_Custom-Nodes/10-6_Python-Templates.html) were introduced. Set these up and Dynamo will automatically add in your boilerplate to every Python node by default, saving you a lot of copy/pasting!

#### Footnote: Good & Bad Importing Habits

Technically, some of the above code does not reinforce best practice when importing libraries. It has been written to introduce the basic concepts and key libraries in a straightforward a way as possible.

For scripts that you write for yourself, the above code should perform perfectly well. However, if you decide to publish a Dynamo that will be distributed to others, this guide encourages you to follow best practice in importing dependencies:

* Avoid importing any classes that are not needed.
* "**From \[namespace\] import \***" is a brute-force import all, which will doubtlessly load in tens or hundreds of unnecessary classes and which will slow down your code. 

