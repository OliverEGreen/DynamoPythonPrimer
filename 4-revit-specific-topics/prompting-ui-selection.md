---
description: Tell me what you need...
---

# 4.10 Prompting UI Selection

#### User-Selection Workflows

Sometimes we might be building a generic tool that requires the user to select Revit elements in the document \(for instance, an element renumbering tool\). It would require an infinite number of customisable filters to let a user select their chosen element\(s\) using logic, however we can skip the whole question by just prompting the user to select something.

#### 'Select Model Elements' is Limited

Of course, there's already a node to let users select elements in Dynamo - Select Model Elements. It's useful as a catch-all; it will let users select elements of any possible category. But what if, instead, we wanted users to only be able to select walls, or detail lines? There is another way.

Revit's [Selection](https://apidocs.co/apps/revit/2019/31b73d46-7d67-5dbb-4dad-80aa597c9afc.htm) class can be used to read the user's currently-selected elements in the active Revit document, or to prompt the user to select via various methods \(by click or by dragging a rectangle\).

#### The ISelectionFilter Interface

This interface can be implemented to restrict the kinds of elements a user can select, using any kind of coded logic. To do this, we need to create a new class which implements the interface.

An instance of this class it then fed as an argument to the [PickElementsByRectangle\(\)](https://apidocs.co/apps/revit/2019/c925f50a-2453-89f7-fd2e-bda44479718d.htm) method. As an example, the code needed to prompt a user to select \(only\) Walls, would be:

```python
#Boilerplate Code

#You'll also want to import the below namespace to get access
#to the ISelectionFilter interface
from Autodesk.Revit.UI.Selection import *

class MySelectionFilter(ISelectionFilter):
	def __init__(self):
		pass
	def AllowElement(self, element):
		if element.Category.Name == "Walls":
			return True
		else:
			return False
	def AllowReference(self, element):
		return False

selection_filter = MySelectionFilter()

walls = uidoc.Selection.PickElementsByRectangle(selection_filter)
OUT = walls
```

The above code shows an example whereby we can prompt the user to only select walls. Dragging a rectangle over non-walls will not select them and they do not get returned by the script.

The [ISelectionFilter](https://apidocs.co/apps/revit/2019/d552f44b-221c-0ecd-d001-41a5099b2f9f.htm) interface has an \_\_init\_\_ method, like any other Python class, and two methods called AllowElement\(\) and AllowReference\(\). The AllowElement\(\) method can be used to define custom logic, returning True when an element meets your criteria. The AllowReference\(\) method can be used to return geometry references, such as edges and faces and, again, it can be built to return True or False as desired.

