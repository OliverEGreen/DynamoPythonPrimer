---
description: A finer-grain version of Revit's Category system
---

# 4.12 Built-In Categories

#### Built-In Categories

The Revit user-interface shows many categories to users, such as Doors, Floors and Generic Models. However, Revit internally keeps track of a much more detailed list of categories, called Built-in categories. The full list of Built-in categories can be found in the [BuiltInCategory Enumeration](https://apidocs.co/apps/revit/2019/ba1c5b30-242f-5fdc-8ea9-ec3b61e6e722.htm) - these are hard coded and we can't create more of them.

#### Retrieving Elements of a BuiltInCategory

Because the list covers nearly 1000 categories, it helps programmers target Revit elements with much greater precision. Built-in categories can be especially useful for FilteredElementCollectors, letting us retrieve highly-specific kinds of elements. For instance, to collect all area tags in a document:

```python
#Boilerplate Code

area_tags = FilteredElementCollector(doc).OfCategory(BuiltInCategory.OST_AreaTags).ToElements()
OUT = area_tags
```

Combined with the usual [boilerplate code](../getting-started/boilerplate-setup-code.md), the above code will rapidly fetch all area tags in a document.  
It is this level of precision which makes BuiltInCategories especially useful when coding.

