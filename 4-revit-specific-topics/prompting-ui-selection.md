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

This interface can be implemented to restrict the kinds of elements a user can select, using any kind of coded logic. It is fed as an argument to the [PickElementsByRectangle\(\)](https://apidocs.co/apps/revit/2019/c925f50a-2453-89f7-fd2e-bda44479718d.htm) method. We can implement this interface like so:

```python
#Boilerplate Code

class MySelectionFilter(ISelectionFilter):
    AllowElement(element):
        if element.Category.Name == "Detail Lines":
            return True
        else:
            return False
    AllowReference(element):
        return False

selection_filter = MySelectionFilter()

detail_lines = Selection.PickElementsByRectangle(selection_filter, "Pick Detail Lines")
OUT = detail_lines
```

Using the UIDocument handle and the Selection class.

The API allows us to filter for specific categories. We need to create a new class to implement this which implements the ISelectionFilter interface.



