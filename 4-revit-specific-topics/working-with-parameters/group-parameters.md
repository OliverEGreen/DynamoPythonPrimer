---
description: "It's nice to feel like a part of something bigger \U0001F30D"
---

# Group Parameters

#### Group Parameters Belong to Groups

In Revit 2018, the developers added a new kind of parameter to the application: the Model Group parameter. When creating a Parameter in the Project Parameters dialog, there was now a category in the Categories list for 'Model Groups'.

#### FamilyInstance/FamilyType is like Group/GroupType

The introductory section on [Family Parameters](instance-parameters.md) has already covered the relationship between FamilyInstance and FamilyType objects. This exact relationship appears again with [Group](https://apidocs.co/apps/revit/2019/2a695dff-8aa5-c266-1d4e-870483e9b5dc.htm) and [GroupType](https://apidocs.co/apps/revit/2019/5ce7e921-2a43-d7f1-8ef9-8a397dd27b75.htm) objects.

Like families, groups have an abstract definition, called a GroupType, which defines all of the elements it contains. Any placed instances of this GroupType in the model are known simply as Groups.

When setting up the parameter in the Project Parameters dialog, there is a toggle to either make it an 'Instance' or a 'Type' parameter - this assigns the parameter to the Group or GroupType depending on which you choose. This also corresponds to the way they are accessed in the Revit API.

#### Accessing Group Parameters

Any instance parameters can be read directly from a group instance. This can either be collecting using a FilteredElementCollector, or passed as an [unwrapped](../unwrapping-revit-elements.md) argument into the Python Script node.

```python
#Boilerplate Code

group = UnwrapElement(IN[0])
parameter = group.LookupParameter("Mark")
```

The above script outputs a [Parameter](https://apidocs.co/apps/revit/2019/333ff41b-e6a7-d959-60bf-c3bfae495581.htm) object, which can be queried for its name or value using one of the typical [parameter conversion methods](instance-parameters.md).

#### Accessing Group Type Parameters

Just like reading a FamilyType's parameters, we first need to get access to the GroupType object. We can either collect all of these using a [FilteredElementCollector](../fetching-revit-elements.md) with the .WhereElementIsElementType\(\) filter applied, or by accessing it from a placed group instance.

```python
#Boilerplate Code

group = UnwrapElement(IN[0])
group_type_id = group.GetTypeId()
group_type = doc.GetElement(group_type_id)

type_parameter = group_type.LookupParameter("Mark")
```

This gets us a Parameter object and, as above, we would use one of the [parameter conversion methods](instance-parameters.md) to then read its value.

