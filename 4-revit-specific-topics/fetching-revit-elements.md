---
description: One of the most powerful tools in Revit API fetches elements - fast!
---

# 4.5 The FilteredElementCollector

#### Introduction

As its name implies, Revit's FilteredElementCollector lets you rapidly search through the Revit document's database for elements, using a custom-defined set of filter rules. You can stack search filters and modifiers together, making the number of custom searches you can undertake practically infinite.

The subject of FilteredElementCollectors is extensive and is thoroughly-covered in the ever-excellent [The Building Coder blog](https://thebuildingcoder.typepad.com/blog/about-the-author.html#5.9). 

#### A Quick Example

FilteredElementCollectors will return a list, either of Element or ElementIds. It's fairly simple to throw a quick one together. For example:

```python
#Boilerplate code
all_furniture = FilteredElementCollector(doc)
all_furniture.OfCategory(BuiltInCategory.OST_Furniture)
all_furniture.WhereElementIsNotElementType()
all_furniture.ToElements()
OUT = all_furniture
```

* This code starts by creating a new FilteredElementCollector instance, which takes the [Revit document](doc-uidoc-app-uiapp.md) as the argument in its constructor.
* The collector is then furniture-refined by specifying a filter - in our example, we only want to return elements of the Furniture category. This is specified as an option in the [BuiltInCategory enumeration](built-in-categories.md).
* Line 4 adds in a further filter - we don't want to include Furniture Family Types in our returned elements, only instances.
* In Line 5 we specify we want the FilteredElementCollector to return us the actual Revit elements \(instead of their ElementIds\).
* Finally, Line 6 uses [OUT](../getting-started/basics-input-and-output.md) to output the collected elements from the node.

It's also possible to condense the above script down to a single line, like so:

```python
#Boilerplate code
all_furniture = FilteredElementCollector(doc).OfCategory(BuiltInCategory.OST_Furniture).WhereElementIsNotElementType().ToElements()
OUT = all_furniture
```

Both scripts will return exactly the same object, so it's down to you to use whichever you prefer - the longer version or the more verbose version.

#### Make a Basic Filter: A Step-By-Step Guide

We've put together a rough step-by-step guide on how to assemble basic filters for elements:

1. Know what you're looking to filter for. If that's elements of a Revit category, find the equivalent [BuiltInCategory ](built-in-categories.md)in the [BuiltInCategory enumeration](https://apidocs.co/apps/revit/2019/ba1c5b30-242f-5fdc-8ea9-ec3b61e6e722.htm). Otherwise, if you're looking for elements of a particular API class, you can use the .OfClass\(\) filter, adding in the Class name as an argument.
2. Do you want to return element instances or their types? For instance, are you looking for all TextNotes in a document \(each might have different text\), or all TextNoteTypes \(e.g. Arial 2.0mm\)? If you want instances, use the .WhereElementIsNotElementType\(\) filter. If you want only types, use the .WhereElementIsElementType\(\) filter. If you want both, don't either of these filters!
3. Do you want to return Revit elements, or the elements' IDs? Finish off your FilteredElementCollector query with either .ToElements\(\) or .ToElementIds\(\).

#### Advanced Filtering

The above is a rough-and-ready guide to constructing a basic FilteredElementCollector. However, there are many more custom filters you can build:

* You can use a ElementLevelFilter to filter for elements hosted at a level, or an ElementWorksetFilter to filter only for elements on a specific workset.
* You can build up custom evaluation rules. Looking only for elements who have a 'Ext' in their Mark parameter value or a Height parameter greater than 3000mm? This is possible.
* This page just scratches the surface of FilteredElementCollectors. We've not even covered QuickFilters and SlowFilters here. Make sure to check out [The Building Coder](https://thebuildingcoder.typepad.com/blog/about-the-author.html#5.9) for extensively-documented details! 

#### Other Notes

In no particular order, some of the quirks or oddities of the collector:

* Worksets can be filtered, but came as a later addition to the API and they have their own special filter method known as the FilteredWorksetCollector.
* You can filter just down to the elements in a specific view if you add in the view's ID as a second argument to the constructor.



